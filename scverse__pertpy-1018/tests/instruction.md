# Issue

**Title:** fix: resolve test-suite warnings

## Description

## Summary

Cleans up the warnings emitted while running the test suite. Running `pytest` on `main` produced **329 warnings**; with this change the runnable subset produces **0**. No library behavior changes.

## Fixed at the source

- **Augur logistic regression** no longer passes the `penalty` argument that scikit-learn 1.8 deprecated (`FutureWarning`, removal in 1.10). The L1/L2 mix is now expressed with `l1_ratio` and the unregularized case with `C`:
  - `l2` → `l1_ratio=0.0` (verified to produce **identical coefficients** to the old default, default `lbfgs` solver, works across the supported sklearn range)
  - `l1` → `l1_ratio=1.0`, `elasticnet` → `l1_ratio=0.5` (both with the `saga` solver)
  - `none`/`None` → `C=np.inf`
- **statsmodels DGE test** sets the negative-binomial `alpha=1.0` explicitly — the previous implicit default — removing the `ValueWarning` raised when the parametrization is collected.
- **Perturbation-space test** wraps the intentional `ensure_consistency=False` `add`/`subtract` calls in `pytest.warns(UserWarning, ...)`, which both silences the leaked warning and asserts the warning is actually raised.

## Filtered as unavoidable third-party noise

Added to the existing `filterwarnings` list in `pyproject.toml` (same pattern already used for ~15 other dependency warnings):

- pydeseq2 *"dispersion trend curve fitting did not converge"* and *"residual degrees of freedom is less than 3"* — emitted on the small synthetic data the Milo and `compare_groups` tests use (this was ~310 of the 329 warnings).
- jaxopt *"no longer maintained"* deprecation notice.
- joblib loky *"A worker stopped while some jobs were given to the executor"* notice.
- formulaic `DataMismatchWarning` from no-intercept contrast handling in the DGE base tests.

## Notes

- The sklearn `penalty` deprecation was fixed in code rather than filtered, since it originates from pertpy's own call.
- 10 failures / 106 errors seen locally are pre-existing network-blocked dataset downloads in this sandbox and are unrelated to this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fa8ed71df95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.