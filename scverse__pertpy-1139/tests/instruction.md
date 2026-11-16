# Issue

**Title:** Speed up Enrichment, perturbation spaces and cell line metadata

## Description

Removes dense intermediates, per-row pandas writes and full AnnData copies across Enrichment, the perturbation spaces and the cell line/MoA annotators (e.g. `Enrichment.score` 88x, `label_transfer` 19-33x, `CellLine.correlate` 6x).
All outputs are bit-identical to main and peak memory is at or below main's.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0465139a0c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.