# Issue

**Title:** Apply the epsilon passed to perturbation_signature to every split

## Description

`perturbation_signature` now applies a user-supplied `epsilon` to the neighbour search of every `split_by` group.
Before, only the first group used it and the rest silently fell back to 0.1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `297302443744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.