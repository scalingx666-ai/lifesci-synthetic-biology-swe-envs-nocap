# Issue

**Title:** Keep a fixed obs column order in from_scanpy

## Description

`from_scanpy` deduplicates sample identifiers and covariates order-preservingly instead of via a set, so `coda.obs` columns come out in a fixed order independent of `PYTHONHASHSEED`.
Values are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72498c050719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.