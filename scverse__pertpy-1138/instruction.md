# Issue

**Title:** Stop simulating discarded counts in make_arviz and trim scGen's training overhead

## Description

`make_arviz` no longer simulates an N x N counts tensor per draw that was then thrown away (scCODA 178 s to 0.55 s, tascCODA 521 s to 0.85 s), and scGen avoids per-step host syncs and eager key splits during training (~1.2x on CPU).
All outputs are bit-identical to main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0465139a0c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.