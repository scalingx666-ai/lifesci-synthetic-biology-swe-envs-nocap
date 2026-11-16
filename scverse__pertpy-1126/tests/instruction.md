# Issue

**Title:** Sample MLPClassifierSpace training cells by inverse class frequency

## Description

`MLPClassifierSpace` now samples training cells by inverse class frequency instead of uniformly (the old weights were 0.5 for every cell).
The documented class-imbalance handling therefore actually balances perturbations during training, which changes the trained embeddings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `297302443744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.