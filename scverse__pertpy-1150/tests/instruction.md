# Issue

**Title:** Fix sparse MMD, bound memory and drop the symmetry assumption in Distance

## Description

Fixes regressions from #1134/#1135 found in review: MMD on sparse layers crashed in `pairwise`/`onesided_distances`, `t_test`/`sym_kldiv`/`ks_test`, `DistanceTest` and Wasserstein allocated far more memory than before (e.g. 440 MB vs 15 MB for a 20k x 2k t-test), and `Edistance.from_precomputed` assumed a symmetric matrix for user-supplied obsp.
All metric values are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27dae8b564c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.