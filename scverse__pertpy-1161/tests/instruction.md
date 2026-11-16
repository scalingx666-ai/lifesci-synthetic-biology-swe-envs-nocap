# Issue

**Title:** Stop rendering scCODA trees inline after saving

## Description

`plot_draw_tree` and `plot_draw_effects` no longer render the tree inline after writing `save`, which required IPython and failed outside notebooks, and the intermediate image for `show_leaf_effects` goes to a temporary directory.
Saving tree plots works from scripts and no longer leaves `tree_effect.png` in the working directory.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72498c050719`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.