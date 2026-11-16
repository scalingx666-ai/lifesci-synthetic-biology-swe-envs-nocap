# Issue

**Title:** Add text and HTML representations to DE model classes

## Description

Inspecting a differential expression model now shows a summary of the input data, the design and the fit state, both as plain text and as an HTML table in Jupyter.

```
>>> edgr
EdgeR
    Data          1,525 obs × 27,085 vars
    Layer         X
    Design        1 + Efficacy + Treatment
    Variables     Efficacy, Treatment
    Coefficients  Intercept, Efficacy[T.PD], Efficacy[T.PR], Efficacy[T.SD], Treatment[T.Chemo]
    Fitted        yes
```

Both representations are driven by a single `_summary()` hook, so `MethodBase` covers the simple tests and `LinearModelBase` adds the design rows.
The HTML uses inline styles relative to the surrounding text, so it renders on light and dark themes and is not affected by the notebook's own table CSS.

`LinearModelBase` gains a public `is_fitted` property to back the `Fitted` row; `PyDESeq2.plot_disp_ests` now uses it instead of probing for `self.dds`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd041e3a9176`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.