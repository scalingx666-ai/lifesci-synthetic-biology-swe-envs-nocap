# Issue

**Title:** Speed up Augur predict

## Description

Speeds up `Augur.predict` with two results-preserving changes.

## Background

Profiling `predict()` on the bundled dataset showed the time is dominated by scikit-learn per-call overhead across the many small models Augur fits (`n_cell_types x n_subsamples x folds`), not the random-forest math itself (tree building was ~1.2 s of ~42 s).

## Changes

1. **NumPy instead of `subsample.to_df()`** in `run_cross_validation`. The DataFrame carries an arrow-backed string column index, which forces scikit-learn to re-validate pandas dtypes and convert the column labels on every fold and every scorer. Passing the dense matrix (with gene names kept separately for the feature-importance table) avoids that. The values, and therefore the results, are identical. ~14% per cross-validation in isolation.

2. **Flattened parallelism.** `predict` now fans every `(cell_type, subsample)` cross-validation task out through a single joblib pool instead of a per-cell-type pool inside a serial loop, so workers no longer idle at each cell-type boundary. Feature selection and eligibility checks still run serially first; submission order is preserved so results regroup per cell type unchanged. 20-30% on the parallel portion in isolation, growing with the number of cell types.

A `threading` backend was also evaluated and rejected (~3x slower, GIL-bound), so loky is kept.

## Results

Back-to-back on the bundled 3-cell-type dataset (best of 3):

| n_threads | before | after |
|---|---|---|
| 4 | 17.0 s | 14.8 s |
| 8 | 13.9 s | 12.2 s |

The end-to-end gain is diluted here by serial fixed costs and only 3 cell types; datasets with more cell types benefit more from change 2.

## Testing

- `pytest tests/tools/test_augur.py` -> 9 passed (the exact-value AUC assertions confirm results are unchanged)
- ruff, ruff-format, mypy pass

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc16ed6c9561`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.