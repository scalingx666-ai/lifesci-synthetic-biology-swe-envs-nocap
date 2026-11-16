# Issue

**Title:** Raise a clear error when a da_nhoods design has no residual degrees of freedom

## Description

.

With one sample per condition, edgeR's `estimateDisp` sets the dispersion to NA and `glmQLFit` then fails with `missing value where TRUE/FALSE needed`, which gives no hint about the actual problem.
`da_nhoods` now checks that the design leaves residual degrees of freedom and raises a `ValueError` pointing at the missing replication, for all three solvers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `557813ceb0f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.