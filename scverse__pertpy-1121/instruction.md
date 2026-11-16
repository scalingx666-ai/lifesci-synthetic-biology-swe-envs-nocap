# Issue

**Title:** Compute every pair in CellLine.correlate instead of mirroring

## Description

`CellLine.correlate` copied `corr[j, i]` into `corr[i, j]`, but expression-vs-metadata correlations are not symmetric, so the lower triangle of every result was wrong and the unmatched call raised `IndexError` when there were more unmatched than matched lines.
Every pair is now computed with scipy's vectorized `pearsonr`, which changes the lower-triangle values to the correct ones.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdd6ebbc40a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.