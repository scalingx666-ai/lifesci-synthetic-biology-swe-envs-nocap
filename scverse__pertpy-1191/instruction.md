# Issue

**Title:** Fix Mixscape barplot layout and class labels

## Description

<!-- Many thanks for contributing to this project! -->

**LLM usage**

- [x] LLM or coding agent used: GPT-5.6 Sol via ChatGPT
- [x] If one was used, I, a human, have reviewed, understood and tested every changed line

**PR Checklist**

- [x] If you've fixed a bug or added code that should be tested, add tests!

**Description of changes**

`Mixscape.plot_barplot()` currently assumes both a fixed 5-column grid shape and the default Mixscape labels `NT` / `KO`.

This causes two independent plotting failures:

1. the subplot row count uses `int(n_genes / 5)`, so fewer than five genes create zero rows and partial final rows can index past the available axes; and
2. results produced with custom `control` or `perturbation_type` labels cannot be plotted because the helper hard-codes `NT` and `KO` when ordering and coloring classes.

This PR:

- computes the number of subplot rows with `ceil(n_genes / 5)`;
- requests a stable 2D axes array with `squeeze=False`;
- hides unused axes in the final partial row; and
- adds `control` and `perturbation_type` arguments (defaulting to `NT` and `KO`) so the plotting helper follows the labels used by `Mixscape.mixscape()`.

Two regression tests cover a six-gene partial grid and custom `CTRL` / `KD` labels.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1502cf00eaa8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.