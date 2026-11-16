# Issue

**Title:** Project Mixscape signatures in float64 again

## Description

Restores float64 projections in `Mixscape.mixscape`, which #1129 accidentally switched to float32 for float32 signatures.
This fixes `plot_perturbscore` failing on pandas 3 in the perturbation efficacy tutorial and restores the previous precision of `pvec`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e63c5d0c51f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.