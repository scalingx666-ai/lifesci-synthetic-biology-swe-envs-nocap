# Issue

**Title:** Skip PyQt6's stubs in mypy

## Description

PyQt6 6.12.0 ships `QtGui.pyi` stubs with `*args, /`, which is invalid syntax and makes mypy abort, so the pre-commit job fails on main and every open PR.
mypy now skips the `PyQt6.*` stubs it reaches through ete4.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b5c53bf0d55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.