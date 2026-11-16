# Issue

**Title:** Resample Y with its own size in Distance.bootstrap

## Description

`Distance.bootstrap` drew Y's bootstrap sample with X's number of cells, so bootstrapped distances and variances were computed on a wrongly sized second group whenever the groups differ in size.
Y is now resampled with its own size, which changes bootstrap means and variances for unequal groups.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27dae8b564c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.