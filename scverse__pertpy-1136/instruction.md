# Issue

**Title:** Add sparse numba kernels for WilcoxonTest and TTest and batch Statsmodels OLS fits

## Description

WilcoxonTest and TTest run on sparse data without densifying (7-28x and 2-6x) and Statsmodels OLS fits all genes with one pseudo-inverse (~60x), lowering peak memory.
Float64 results match main; float32 input is now computed in float64, which moves Wilcoxon p-values by up to ~2e-4 relative toward the float64 reference.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0465139a0c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.