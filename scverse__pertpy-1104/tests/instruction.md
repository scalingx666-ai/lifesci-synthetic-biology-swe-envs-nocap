# Issue

**Title:** Keep scCODA and tascCODA working under numpyro 0.22

## Description

numpyro 0.22 enables distribution validation by default, which rejects the fractional counts scCODA creates with its 0.5 pseudocount and makes `run_nuts()` fail with "Cannot find valid initial parameters".
The count likelihood now opts out of validation, since its log-prob is well defined for fractional counts, and the prior predictive rounds the number of trials.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af8a836aab35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.