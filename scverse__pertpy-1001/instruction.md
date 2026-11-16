# Issue

**Title:** add MiloDE

## Description

.

Implements miloDE-style per-neighbourhood differential expression testing as `Milo.de_nhoods`.  Pure Python, no edgeR.

## API

```python
import pertpy as pt
import scanpy as sc

adata = pt.dt.kang_2018()                       # 8 patients × ctrl/stim, raw counts in .X
adata.layers["counts"] = adata.X.copy()
adata.obs["sample"] = adata.obs["replicate"].astype(str) + "_" + adata.obs["label"].astype(str)
sc.pp.normalize_total(adata); sc.pp.log1p(adata); sc.pp.pca(adata)
sc.pp.neighbors(adata, use_rep="X_pca", n_neighbors=100)
sc.tl.umap(adata)

milo = pt.tl.Milo()
mdata = milo.load(adata)
milo.make_nhoods(mdata["rna"], prop=0.1)
mdata = milo.count_nhoods(mdata, sample_col="sample")
milo.build_nhood_graph(mdata)

# Per-nhood DE -- same column names as the rest of pertpy DE, plus the
# spatial-FDR axis miloDE introduces.
de = milo.de_nhoods(
    mdata,
    design="~label",
    column="label", baseline="ctrl", group_to_compare="stim",
    solver="pydeseq2",          # or "statsmodels" (auto NB-GLM + size-factor offset)
    layer="counts",
)
# Long DataFrame: nhood, variable, log_fc, p_value, adj_p_value,
# pval_corrected_across_nhoods, test_performed.

# Visualize one gene's per-nhood logFC -- one line:
milo.plot_de_nhood_graph(mdata, de, gene="ISG15", min_size=2)

# Per-nhood volcano with the existing DE plot (column names already match):
nh_df = de.loc[de["nhood"] == mdata["milo"].var_names[0]].dropna(subset=["adj_p_value"])
pt.tl.TTest(mdata["milo"]).plot_volcano(nh_df, log2fc_thresh=0.5)
```

`milo.plot_de_nhood_graph(mdata, de, gene="ISG15")` on kang_2018 (canonical IFN-β response gene; expected strong positive logFC in many nhoods):

![nhood graph](https://github.com/scverse/pertpy/raw/feat/milode-de-nhoods/docs/_static/docstring_previews/milo_de_nhoods_nhood_graph.png)

## What it does

For each nhood: pseudobulks cells by sample via `sc.get.aggregate`, fits the existing pertpy DE model (`PyDESeq2` or `Statsmodels`), and applies the two-axis correction miloDE uses — BH across genes within each nhood, density-weighted BH across nhoods per gene (same correction `da_nhoods` uses, now factored into a shared `_weighted_bh` helper).  Nhoods that fail validity (too few samples per condition, rank-deficient design) are skipped and flagged in `test_performed`; one summary log line is emitted at the end rather than one per skipped nhood.

`plot_de_nhood_graph` is the DE-side counterpart of `plot_nhood_graph`: takes the long DataFrame plus a gene name and renders the nhood graph colored by that gene's logFC, masking nhoods with `pval_corrected_across_nhoods > alpha`.  The shared rendering body is factored into a private helper used by both.

## Validation against miloDE R

Ran the R package on the same synthetic data + nhood structure (71 nhoods × 200 genes, planted DE in one population):

| metric | value |
|---|---|
| nhoods passing `test_performed` (R / Py / both) | 71 / 71 / 71 |
| Spearman(logFC) across genes per nhood | **median 0.996** (min 0.978) |
| Spearman(pvalue) across genes per nhood | median 0.934 |
| sign-concordance on R-significant entries (padj<0.1) | **282 / 282 = 1.000** |
| Spearman(pval_corrected_across_nhoods) per planted gene | median 0.919 |

Remaining differences are NB-GLM Wald (PyDESeq2) vs edgeR's QLF on small samples.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f52cb9996637`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.