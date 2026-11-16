# Issue

**Title:** Seed the control gene sampling of Enrichment.score

## Description

`Enrichment.score` gains a `random_state` argument (`RandomStateLike`, default 0, as in the perturbation space tools) that seeds the control-gene sampling of the seurat method.
Seurat-style scores are now reproducible across calls.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7237704121bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.