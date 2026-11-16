# Issue

**Title:** Support sparse matrices in perturbation space helpers

## Description

Perturbation space clustering, evaluation, centroids, similarity and `compute_control_diff` now accept sparse `.X` and layers instead of crashing on a 0-d object array.
Sparse matrices are passed straight to scikit-learn and only the parts that need dense data are densified.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `992dbe992f00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.