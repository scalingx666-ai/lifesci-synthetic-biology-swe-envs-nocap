# Issue

**Title:** Speed up Mixscape, Mixscale, guide assignment and CINEMA-OT

## Description

Replaces element-wise LIL assembly, per-target AnnData copies and dense N x N intermediates in Mixscape/Mixscale, guide assignment and CINEMA-OT with sparse stacking, numba kernels and batched DE calls (e.g. `mixscale` 11x, `perturbation_signature` 6x on sparse data, `assign_to_max_guide` 120x).
Outputs are bit-identical to main and peak memory is at or below main's.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0465139a0c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.