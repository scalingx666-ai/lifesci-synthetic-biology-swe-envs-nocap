# Issue

**Title:** Fit Mixscape's two-component mixtures with a numba EM and trim lda

## Description

Replaces Mixscape's per-target sklearn GaussianMixture fits with a numba EM (mixscape 35 s to 6 s at 100k cells), computes each target's PCA once in `lda` (1.5x, 2.8x with `split_by`) and drops CINEMA-OT's dense kNN graph (half the memory).
Results match main except that dense float32 signatures are fitted in float64, which changed 2 of ~80k KO/NP labels in testing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `992dbe992f00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.