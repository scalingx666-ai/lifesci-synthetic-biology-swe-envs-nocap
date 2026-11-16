# Issue

**Title:** Make class-balanced sampling in MLPClassifierSpace opt-in

## Description

#1126 turned on inverse-frequency sampling of training cells, which was documented but had never been active, and on the Norman tutorial it changes the embedding substantially (mean per-perturbation cosine 0.93 to the previous embedding, programme silhouette +0.12 to -0.11).
`MLPClassifierSpace.compute` gains `balance_classes` (default `False`), so the default embedding is bitwise identical to before #1126 and balancing is available on request.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27dae8b564c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.