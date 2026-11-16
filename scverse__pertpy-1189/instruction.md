# Issue

**Title:** Separate Mixscape min_cells from min_de_genes to match Seurat

## Description

<!-- Many thanks for contributing to this project! -->

**LLM usage**

- [x] LLM or coding agent used: GPT-5.6 Sol via ChatGPT
- [x] If one was used, I, a human, have reviewed, understood and tested every changed line

**PR Checklist**

- [x] If you've fixed a bug or added code that should be tested, add tests!

**Description of changes**

`Mixscape.mixscape()` currently uses `min_de_genes` for two independent thresholds:

1. the minimum number of DE genes required to classify a perturbation, and
2. the minimum number of cells that must remain assigned to the perturbed class during the iterative KO/NP classification.

The current Seurat reference implementation separates these concepts as `min.de.genes` and `min.cells`. Seurat fixed the same coupling in satijalab/seurat#10299 in February 2026.

This PR adds `min_cells=5` to `Mixscape.mixscape()` and uses it for the cell-count safeguard while leaving `min_de_genes` responsible only for the DE-gene threshold. The default is 5, matching Seurat, so default behavior is unchanged.

A regression test deliberately sets `min_de_genes` and `min_cells` to different values and verifies that changing one no longer changes the semantics of the other.

**Technical details**

The behavioral change is limited to calls that explicitly use a non-default `min_de_genes` value. Previously, for example, `min_de_genes=10` also implicitly required at least 10 cells to remain classified as perturbed. After this change, the cell threshold is controlled independently through `min_cells`.

Validation completed:

- upstream CI test matrix passes on Python 3.13 stable, Python 3.14 stable, and Python 3.14 pre-release dependencies
- Codecov reports all modified and coverable lines are covered by tests
- `ruff check` passes
- `ruff format` passes
- build and tutorial workflows pass

The remaining `Pre-commit checks` failure is unrelated to this PR: `mypy` currently fails while parsing `PyQt6/QtGui.pyi` with 16 syntax errors. The same failure is present on the current `main` branch scheduled Test workflow at commit `9b5c53b`.

**Additional context**

Reference fix in Seurat: satijalab/seurat#10299.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4f0802072af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.