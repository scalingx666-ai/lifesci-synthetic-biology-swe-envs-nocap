# Issue

**Title:** Add plot_ma for DGE results

## Description

Adds `plot_ma` to `MethodBase`, the pertpy equivalent of edgeR's `plotSmear` and DESeq2's `plotMA`: mean expression against the log2 fold change, highlighting the variables the test called significant.
As #803 puts it, the volcano plot carries no information about expression range, so lowly expressed hits are indistinguishable from well expressed ones.

The mean column differs per method, so it is detected from the results — `baseMean` for PyDESeq2, `logCPM` for edgeR — and `mean_col` covers anything else.
The x-axis is log-scaled for linear mean columns and left alone for those already on a log scale.

Verified end-to-end against both backends, not just the unit tests: PyDESeq2 picks up `baseMean` with a log x-axis, edgeR picks up `logCPM` with a linear one.
The docstring preview is EdgeR on `zhang_2021`, the same example the other DGE plots use.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e62625a2dbd2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.