# Issue

**Title:** PyDESeq2: optional apeGLM LFC shrinkage

## Description

Addresses #903.

Adds an opt-in `lfc_shrink` kwarg on PyDESeq2 contrast tests. When set to a coefficient name from the fitted LFC matrix, applies pydeseq2's apeGLM shrinkage after `summary()`.

Opt-in because apeGLM shrinks individual coefficients rather than arbitrary contrasts, so the right coefficient can't be inferred from a numerical contrast vector.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2569fc71012`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.