# Issue

**Title:** Add plot_credible to plot_effects_umap

## Description

Cell types without a credible effect carry an effect of exactly zero (this is how `credible_effects` decides credibility), so they were colored as if a zero effect had been measured.
With `plot_credible=True` they are masked to NaN and rendered in the `na_color` of `sc.pl.umap`, leaving only credible effects colored.

Defaults to `False` to keep existing plots unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71b576168764`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.