# Issue

**Title:** Keep R from loading the system libpython in the tutorial notebooks

## Description

On Ubuntu 26.04, which is now ubuntu-latest, R prepends the system library directory to LD_LIBRARY_PATH, so joblib's worker processes load Ubuntu's libpython3.14 instead of setup-python's and cannot import joblib. Presetting R_LD_LIBRARY_PATH to R's own lib directory fixes the milo and differential gene expression notebooks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f19ae9b71367`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.