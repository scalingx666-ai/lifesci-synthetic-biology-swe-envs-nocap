# Issue

**Title:** Fix tascCODA returning no credible effects (theta collapse)

## Description

## What

 — tascCODA returned **zero credible effects** on data where it should recover them.

## Root cause

The global spike-and-slab mixing weight `theta ~ Beta(1, d)` **collapses to its prior** (median ≈ 0.01) under numpyro NUTS. Because the credibility threshold is

```
delta = 1/(l0 - l1) * log(1/p_t - 1),   p_t = (theta*l1/2) / (theta*l1/2 + (1-theta)*l0/2)
```

a near-zero `theta` is a *double* failure: it shrinks `b_tilde = (1-theta)*spike + theta*slab` toward the spike (≈0) **and** sends `delta → ∞`. Nothing can clear the threshold.

This is the model's **true marginal posterior**, not a numpyro bug. A single global `theta` gates a high-dimensional slab, so the low-`theta` funnel mouth (slab unconstrained) carries almost all the marginal volume — confirmed by Betancourt's incomplete-reparameterization result: no practitioner-applicable reparameterization changes `theta`'s marginal, and the slab is already non-centered.

**Why upstream "works":** the reference TFP implementation samples with a *fixed identity mass matrix* and a *fixed 10-leapfrog trajectory* started at `theta = 0.5`, so it physically cannot traverse to the funnel and stays pinned near init (back-solving its reported `Delta = 0.066` gives `theta ≈ 0.34`). numpyro NUTS (adaptive mass + dynamic trajectories) mixes well enough to find the genuinely-collapsed posterior. In other words, **the published results were computed with `theta` effectively fixed, never inferred** — and the canonical spike-and-slab LASSO (Ročková–George) is itself estimated by MAP/EM precisely because full-Bayes MCMC on this posterior is multimodal/prohibitive.

## Fix

Hold `theta` fixed via `numpyro.deterministic` at `pen_args["theta"]` (default **0.5**, the reference's operating point; settable, e.g. `0.34` to match upstream's exact `delta`).

This is the minimal change that reproduces the paper's effective behavior. **Unchanged:** `samples["theta"]` (still present, as a constant), the `delta` credibility rule, the summary layout, arviz dims/coords, and `param_names`. The now-dead `d = D*(T - n_ref)` and the stale `theta` init entry are removed.

## Validation (tutorial data, `formula="Health"`, `phi=0`, automatic reference)

| scenario | θ median | credible | recovered |
|---|---|---|---|
| **before** (sampled θ) | 0.01 | 0 / 74 | — |
| full 3-group, θ=0.5 | 0.500 | 3 / 148 | **Immune, B cells, TA cells** |
| 2-group, θ=0.5 | 0.500 | 1 / 74 | TA cells |
| 2-group, θ=0.34 (`pen_args`) | 0.340 | 1 / 74 | TA cells |

Stable across seeds {0, 7, 42, 123} and across θ∈[0.34, 0.5]; `delta` is finite. The recovered set matches the effects reported in the issue.

## Trade-off / faithfulness

`theta` is no longer a random variable. That is a deliberate, documented deviation from the *generative* model — but it is faithful to the published *results*, which depend on `theta` staying near 0.5. Keeping `theta` sampled and instead crippling the numpyro sampler to mimic upstream's non-convergence would be fragile and init-dependent; a regularized-horseshoe redesign would be robust but is a different method (no `theta`/`delta`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1ab3899afc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.