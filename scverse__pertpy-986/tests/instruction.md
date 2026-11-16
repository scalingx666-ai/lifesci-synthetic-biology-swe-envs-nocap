# Issue

**Title:** Milo cleanup: address #181

## Description

.

- Rename `add_covariate_to_nhoods_var` → `add_covariate_to_nhoods_obs` (destination is `mdata['milo'].obs`). Old name kept as deprecated alias.
- Preserve categorical dtypes when copying covariates (previous `.astype('str')` silently turned them into object, breaking downstream plots).
- `plot_nhood_counts_by_cond`: clear error when `test_var` column is missing; coerce object columns to category.
- `da_nhoods`: deprecate `subset_samples` (causes SpatialFDR bugs in edge cases — use contrasts or subset before kNN). Validate contrast levels against the design columns for both edgeR and pydeseq2 so the failure is informative instead of an opaque rpy2/pydeseq2 traceback.

Adds `scverse-misc` to dependencies for `deprecated` / `deprecated_arg`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `69318428313f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.