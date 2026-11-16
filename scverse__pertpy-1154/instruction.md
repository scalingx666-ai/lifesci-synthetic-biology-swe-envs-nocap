# Issue

**Title:** Handle one-cell and empty groups in the vectorized t-test

## Description

`TTest.compare_groups` crashed with `ZeroDivisionError` since #1136 when a comparison group had one cell or none.
The kernel now returns scipy's values (variance 0 for one cell, NaN for an empty group) for dense and sparse input.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f60cc1c2b58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.