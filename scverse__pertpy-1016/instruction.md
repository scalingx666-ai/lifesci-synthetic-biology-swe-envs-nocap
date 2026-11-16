# Issue

**Title:** Fix tascCODA always returning insignificant results

## Description

## What

Fixes tascCODA always returning insignificant results, plus a `run_hmc` crash.

### 1. NaN node-effect medians (the main bug)

The arviz 1.0 migration (#911) recomputed the posterior median in `summary_prepare` via:

```python
summ["median"] = posterior[var_names].median(dim=["chain", "draw"]).to_dataframe().stack().reindex(summ.index)
```

`.to_dataframe().stack()` produces a tuple MultiIndex (e.g. `("A", "x", "n0", "alpha")`) that never matches arviz's string row labels (e.g. `"b_tilde[x, n0]"`), so `reindex(summ.index)` fills the entire `median` column with **NaN**.

tascCODA decides node credibility with `|median| > delta` (`__complete_node_df`), so NaN medians made **every** effect non-credible regardless of the data — i.e. "always insignificant".
scCODA is unaffected because it selects effects via inclusion probabilities, not the median, which is why only tascCODA broke.

The fix computes the medians positionally, which matches `az.summary`'s row order exactly (rows ordered by `var_names`, then C-order of each variable's dims — identical to `DataArray.values.flatten()`).

### 2. `run_hmc` rng-key `TypeError`

`run_hmc` converted `rng_key` to a JAX key *before* handing it to `set_init_mcmc_states`, which seeds a NumPy generator and therefore needs an int — raising `TypeError: SeedSequence expects int ...`.
It now keeps the int seed for the NumPy generator and derives the JAX key separately, mirroring `run_nuts`.

## Not included here

While verifying this, I found a deeper, separate problem: even with medians fixed, the (correct) spike-and-slab model recovers no credible effects because the global `theta` collapses to its prior under numpyro's samplers. That needs a model-level change and is tracked in #1015 with the full analysis.

## Tests

No new test is added: the meaningful assertion (tascCODA recovers known credible effects) is blocked by #1015, and asserting only that medians are non-NaN isn't worth pinning.
Existing `tests/tools/_coda/test_tasccoda.py` passes, and `run_hmc` now runs end-to-end.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `652395a9fd61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.