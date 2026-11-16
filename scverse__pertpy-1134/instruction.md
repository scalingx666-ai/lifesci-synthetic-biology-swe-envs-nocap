# Issue

**Title:** Speed up Distance, DistanceTest and DistanceSpace

## Description

Removes per-pair and per-permutation pandas work from `Distance.pairwise`/`onesided_distances` and `DistanceTest`, and adds numba kernels for the KS statistic and precomputed e-distances (e.g. `DistanceTest` 35x, `ks_test` 27x, `pairwise` `t_test` 13x) without raising peak memory.
Results match main to rounding, except float32 precomputed e-distances, which are now summed in float64 (up to ~5e-5 relative, no p-value changes).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b56f68f9e997`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.