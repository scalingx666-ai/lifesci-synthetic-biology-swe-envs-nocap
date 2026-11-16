# Issue

**Title:** Fix plot_multicomparison_fc ValueError with default figsize

## Description

Seaborn heatmap hides tick labels when the figure is too narrow, causing a ValueError when plot_multicomparison_fc tries to place significance markers. The code looks up gene names in x_labels, but those labels are missing when the heatmap suppresses them.

This sets xticklabels=True and yticklabels=True as defaults so tick labels are always visible. Users can still override these via heatmap_kwargs if needed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4e81fe91376`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.