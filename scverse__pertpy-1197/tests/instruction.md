# Issue

**Title:** Align Mixscape marker selection and classification with Seurat

## Description

<!-- Many thanks for contributing to this project! -->

**LLM usage**

- [x] LLM or coding agent used: GPT-6 via ChatGPT
- [x] If one was used, I, a human, have reviewed, understood and tested every changed line

Opened as a draft pending human review of the final diff.

**PR Checklist**

- [x] Tests added for changed behavior
- [x] Public API docstrings updated

**Description of changes**

Mixscape currently selects DE markers using Scanpy's default BH adjustment and approximate log-fold changes, without the detection-fraction and minimum-group-size defaults used by Seurat's `TopDEGenesMixscape()` / `FindMarkers()`.

This PR aligns **the marker-selection stage** with those Seurat defaults:

- Bonferroni adjustment over the full feature set;
- `min.pct = 0.1` (detected in at least 10% of either group);
- `min.cells.group = 3` for both target and control groups; and
- Seurat-style average log2 fold change from log1p-normalized expression, including its pseudocount.

The Scanpy statistical testing backend remains unchanged. **This does not claim exact R/Scanpy Wilcoxon numerical parity.** These are intentionally behavior-changing marker-selection defaults and can affect downstream Mixscape classifications.

**Technical details / validation**

- Keeps sparse matrix support, including CSR arrays, and honors the DE layer.
- Adds regression cases for each filter and updates two synthetic end-to-end tests to provide sufficiently strong perturbation signal under Bonferroni.
- Full local Mixscape module: **18 passed** (headless Matplotlib backend).
- Ruff, format, syntax, and whitespace checks passed.
- Independent Adamson 2016 pilot check: BHLHE40 selected markers changed from **72** (previous helper) to **37** (new helper), matching the independent Seurat-style selection audit.
- A separate Papalexi 2021 RNA-only marker audit showed an illustrative **12,448 -> 5,793** raw target-marker relations with the same selection semantics. This is a *selection-stage comparison using Scanpy test statistics*, not an R/Seurat end-to-end replication.

No new dependencies.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b29fc5a05d2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.