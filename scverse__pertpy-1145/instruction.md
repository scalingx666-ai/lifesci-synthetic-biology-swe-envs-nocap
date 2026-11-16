# Issue

**Title:** Keep control cells in Mixscape.lda when the label has spaces

## Description

`Mixscape.lda` and `plot_lda` now select control cells by their label rather than by the global class, so control labels containing spaces (e.g. "Non Targeting") are no longer dropped.
Before, the LDA was fit on perturbed cells only, or failed outright.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d8628d501c3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.