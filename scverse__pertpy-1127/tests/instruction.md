# Issue

**Title:** Match PRISM drug names case-insensitively without mutating the cache

## Description

`CellLine.annotate_from_prism` now matches drug names case-insensitively on a copy of the PRISM table.
Drugs with uppercase PRISM names such as ABT-737 are annotated instead of getting NaN, and the cached `drug_response_prism` is no longer modified.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `297302443744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.