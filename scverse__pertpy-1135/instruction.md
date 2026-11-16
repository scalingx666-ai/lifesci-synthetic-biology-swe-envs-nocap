# Issue

**Title:** Add numba kernels for MMD, mean_var_distribution and nb_ll and bucket Wasserstein shapes

## Description

Replaces sklearn/statsmodels/ott hot paths in MMD (no n x n matrices, 6-70x), `mean_var_distribution` (25x), `nb_ll` (18x) and Wasserstein (3x, fewer JIT recompiles) with numba kernels, lowering peak memory.
Float32 MMD/Wasserstein values move ~1e-7 to 1e-5 toward float64 and `nb_ll` changes more because it now fits the overdispersed genes main's BFGS dropped; `DistanceTest` calls are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1c071a8967c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.