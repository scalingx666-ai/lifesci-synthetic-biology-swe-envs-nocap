# Issue

**Title:** Speed up Statsmodels contrasts, PermutationTest, Dialogue and Augur

## Description

Vectorizes Statsmodels contrast testing (11-20x) and PermutationTest's default statistic (~1.8x), fits Dialogue's per-gene mixed models without formula parsing (1.45x end to end) and cuts AnnData copies in Augur's subsampling (1.65x in permute mode).
Results are bitwise identical to main; Statsmodels p-value columns are now float64 instead of object.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c75b0641cf6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.