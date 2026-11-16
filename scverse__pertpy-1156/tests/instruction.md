# Issue

**Title:** Make Dialogue's HLM robust to degenerate rows and covariates

## Description

Dialogue's per-gene HLM now returns NaN estimate and p-value for constant or collinear genes instead of a huge finite estimate, drops unused categorical levels and zero-variance covariate columns instead of NaN-ing a whole pair block, and accepts an empty covariate frame.
Results for non-degenerate genes are bitwise unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f60cc1c2b58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.