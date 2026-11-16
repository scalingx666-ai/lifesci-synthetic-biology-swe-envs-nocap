# Issue

**Title:** Fix multiple temperature scaling in sample_non_deterministic()

## Description

Ensures that temperature scaling is applied only once by moving it inside softmax() instead of modifying logits multiple times. Fixes issue #19.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2842ef05444d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.