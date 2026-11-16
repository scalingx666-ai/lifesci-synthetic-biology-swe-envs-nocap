# Issue

**Title:** Reject all-zero contrasts in test_contrasts

## Description

.

Requesting an interaction contrast on a model fit without the interaction term silently produced all-NaN results. `test_contrasts` now raises a `ValueError` pointing at the likely cause (contrast lies in the null space of the design matrix).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a767ba7109c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.