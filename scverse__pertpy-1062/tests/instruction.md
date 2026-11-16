# Issue

**Title:** Rename DistanceTest alpha to padj_threshold

## Description

Aligns `DistanceTest` with the significance threshold naming introduced in #974, where `alpha` became `padj_threshold` in Milo, the DGE base and enrichment.
`alpha` stays accepted via `deprecated_arg` and now emits a `FutureWarning`.

DIALOGUE is left alone, as requested in the issue.

Two things worth a look:
- The attribute `DistanceTest.alpha` became `DistanceTest.padj_threshold` without an alias, since only the constructor argument is deprecated.
- The distance tests tutorial passes `alpha=0.0015`; it lives in the `pertpy-tutorials` submodule, so it keeps working through the deprecation and needs a separate update there.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71b576168764`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.