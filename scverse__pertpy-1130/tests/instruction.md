# Issue

**Title:** Dispatch Mixscale's sparse helpers for scipy sparse matrices too

## Description

Mixscale's sparse helpers are now registered for scipy sparse matrices as well as sparse arrays.
`scale=False` works on csr_matrix layers and matches the R reference.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `297302443744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.