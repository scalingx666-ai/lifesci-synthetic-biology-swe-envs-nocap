# Issue

**Title:** Batch Milo's neighbourhood refinement and pydeseq2 likelihood-ratio fits

## Description

Vectorizes `make_nhoods`' index refinement (3.5x) and fits the pydeseq2 likelihood-ratio tests of all neighbourhoods jointly in `da_nhoods` (~3-7x), with identical neighbourhoods and significance calls and unchanged peak memory.
Adds `scipy>=1.16` as a dependency for the batched linear solve.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `297302443744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.