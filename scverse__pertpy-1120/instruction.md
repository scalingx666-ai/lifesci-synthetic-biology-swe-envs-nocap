# Issue

**Title:** Compute evaluate_clustering's ASW on the precomputed cell distances

## Description

`evaluate_clustering` passed its precomputed distance matrix to `silhouette_score` with `metric="euclidean"`, so ASW was computed on rows of the distance matrix instead of on the cells.
It now uses `metric="precomputed"`, which changes reported ASW values to the correct silhouette score.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdd6ebbc40a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.