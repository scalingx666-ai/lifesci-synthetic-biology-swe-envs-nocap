# Issue

**Title:** DIALOGUE: from-scratch port of the R reference (PMD + HLM + iterative NNLS)

## Description

Rewrites pertpy's DIALOGUE tool as a faithful Python port of [`livnatje/DIALOGUE`](https://github.com/livnatje/DIALOGUE) on AnnData. Replaces ~1100 lines of the previous attempt with a from-scratch implementation that goes through every step the R package does — PMD weight fitting, empirical-p permutation test, per-cell-type partial-Spearman gene signatures, cross-celltype HLMs, Fisher-combined gene p-values, iterative NNLS rescue of the final per-cell scores — all wired up through one user-facing class. Closes the gaps documented in #731.

## API

```python
import pertpy as pt

dl = pt.tl.Dialogue(
    celltype_key="cell.subtypes",
    sample_key="sample",
    cell_quality_key="cellQ",
    n_programs=3,
)
dl.run(adata)                                # fit_programs + test_celltype_pairs + refine_scores
adata.obsm["X_dialogue"]                     # final per-cell program scores
adata.obs[["mcp_0", "mcp_1", "mcp_2"]]       # convenience columns
adata.uns["dialogue"]                        # weights, signatures, gene_pvalues, pair_results, …

dl.test_phenotype_association(adata, condition_key="path_str")
dl.get_program_genes(adata, program="MCP1", celltype="TA2")
dl.find_extreme_score_genes(adata, program="MCP1", fraction=0.1)
dl.plot_split_violins(adata, condition_key="path_str", program="MCP1")
dl.plot_pairplot(adata, color="clinical.status", program="MCP1")
```

Old method names (`calculate_multifactor_PMD`, `multilevel_modeling`, `test_association`, `get_extrema_MCP_genes`, `get_mlm_mcp_genes`) are removed — the previous API was buggy enough that we treat this as a fresh start.

## R-vs-Python comparison (defaults: k=3, n_permutations=100, conf=cellQ, covar=cellQ + tme_qc)

Run on `pt.dt.dialogue_example()` (5,156 cells, 4 cell types, 29 samples).

### PMD weights cosine similarity vs. R

| celltype | MCP1 | MCP2 | MCP3 |
|----------|------|------|------|
| CD8+ IELs | 0.9997 | 0.9995 | 0.9980 |
| CD8+ LP | 0.9996 | 0.9990 | 0.9984 |
| Macrophages | 0.9998 | 0.9990 | 0.9991 |
| TA2 | 0.9998 | 0.9990 | 0.9976 |

### Empirical p-values (programs × pairs)

**Python**:

|      | CD8+ IELs_CD8+ LP | CD8+ IELs_Macrophages | CD8+ IELs_TA2 | CD8+ LP_Macrophages | CD8+ LP_TA2 | Macrophages_TA2 |
|:-----|--:|--:|--:|--:|--:|--:|
| MCP1 | 0.010 | 0.010 | 0.010 | 0.010 | 0.010 | 0.010 |
| MCP2 | 0.010 | 0.040 | 0.188 | 0.050 | 0.119 | 0.208 |
| MCP3 | 0.010 | 0.129 | 0.099 | 0.059 | 0.149 | 0.010 |

**R**:

|      | CD8+ IELs_CD8+ LP | CD8+ IELs_Macrophages | CD8+ IELs_TA2 | CD8+ LP_Macrophages | CD8+ LP_TA2 | Macrophages_TA2 |
|:-----|--:|--:|--:|--:|--:|--:|
| MCP1 | 0.042 | 0.042 | 0.042 | 0.042 | 0.042 | 0.042 |
| MCP2 | 0.042 | 0.042 | 0.145 | 0.045 | 0.042 | 0.045 |
| MCP3 | 0.042 | 0.042 | 0.045 | 0.349 | 0.153 | 0.042 |

Both methods flag MCP1 as significant across every pair and produce the same qualitative pattern on MCP2/MCP3.

### Refined per-cell program scores: |correlation| with R reference

| celltype | MCP1 | MCP2 | MCP3 |
|----------|------|------|------|
| CD8+ IELs | 0.990 | 0.939 | 0.909 |
| CD8+ LP | 0.995 | 0.934 | 0.929 |
| Macrophages | 0.993 | 0.975 | 0.975 |
| TA2 | 0.984 | 0.731 | 0.966 |

End-to-end runtime: ~120 s with the full reference defaults.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `064d70533b6c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.