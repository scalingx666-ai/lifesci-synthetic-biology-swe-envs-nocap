# Issue

**Title:** Make scCODA results writable to h5mu

## Description

.
`summary_prepare` now returns plain float64 DataFrames instead of arviz 1.x's `SummaryDataFrame` subclass with nullable Float64 columns, so scCODA and tascCODA results stored in `varm` can be written with `write_h5mu` again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a130d0f1b2a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.