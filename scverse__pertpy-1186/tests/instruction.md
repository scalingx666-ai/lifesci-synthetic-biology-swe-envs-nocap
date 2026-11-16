# Issue

**Title:** Add the Human Cytokine Dictionary as pt.md.Cytokine

## Description

.
Adds `pt.md.Cytokine`, whose `gene_sets` returns the genes each cytokine regulates in a PBMC cell type as `targets` for the `Enrichment` tests, so users get the dictionary without the 3.4 GB DEG table.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6feb8d6d8285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.