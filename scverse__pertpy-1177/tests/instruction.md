# Issue

**Title:** Make Dialogue reproduce the R DIALOGUE reference end to end

## Description

. Dialogue now reproduces livnatje/DIALOGUE stage by stage, with REML mixed models and Satterthwaite t-tests like lmerTest, R's PMD penalty, permutation test, cell-type pruning, sample order, signature selection and one-sided gene p-values, and DIALOGUE.pheno semantics in test_phenotype_association. On four public datasets every gene set, refined score and phenotype z-score matches R while runs take seconds instead of minutes; the regenerated tutorial is scverse/pertpy-tutorials#80.

Accuracy against R (R 4.5.3, lme4 2.0.6, lmerTest 3.2.1; k = 3, 100 permutations, 30 PCs, 100 genes per signature). Jaccard is over all program-direction-cell-type gene lists, correlation over refined per-cell scores per program and cell type.

| Dataset | Metric | pertpy main | pertpy #1177 |
|---|---|---|---|
| dialogue_example (5,156 cells, 4 cell types, 29 samples) | gene sets sig1 / sig2 Jaccard | 0.77 / 0.62 (min 0.00) | 1.00 / 1.00 |
| | refined score correlation | mean 0.96, min 0.71 | 1.00, max diff 3e-6 |
| | phenotype z-scores | 14% too large, max diff 1.0 | identical to 3 decimals |
| DIALOGUE toy example (5,374 cells, 3 cell types, 86 samples) | gene sets sig1 / sig2 Jaccard | 0.50 / 0.47 (min 0.03) | 1.00 / 1.00 |
| | refined score correlation | mean 0.88, min 0.54 | 1.00 |
| | phenotype z-scores | 1.9x too large, max diff 4.6 | identical |
| Kang 2018 (24,541 cells, 7 cell types, 16 samples) | gene sets sig1 / sig2 Jaccard | 0.39 / 0.39 (min 0.00) | 1.00 / 1.00 |
| | refined score correlation | mean 0.26, min -0.97 | 1.00 |
| | phenotype z-scores | 23x too large, max diff 321 | identical |
| Stephenson 2021 (27,490 cells, 5 cell types, 68 samples) | gene sets sig1 / sig2 Jaccard | 0.02 / 0.00 | 1.00 / 1.00 |
| | refined score correlation | mean -0.60, min -0.98 | 1.00 |
| | phenotype z-scores | 1.5x too large, max diff 4.0 | identical |

With R's phase 1 or phase 2 outputs injected, pertpy's pair z-scores are within 2e-3 of lmerTest's and gene p-values within 1e-15 of R's on every dataset; the mixed-model kernel itself matches lmerTest to 1e-7 relative on sample-level, cell-level and singular designs. End to end only the permutation p-values differ, by RNG, and they select the same cell types.

Wall time of the full pipeline including phenotype association, warm numba cache, quiet 64-core machine, and peak RSS:

| Dataset | R DIALOGUE | pertpy main | pertpy #1177 |
|---|---|---|---|
| dialogue_example | 169 s, 1.39 GB | 6.3 s, 870 MB | 3.4 s, 803 MB |
| DIALOGUE toy example | 124 s, 0.91 GB | 3.3 s, 830 MB | 2.6 s, 727 MB |
| Kang 2018 | 931 s, 2.54 GB | 25 s, 1585 MB | 12 s, 815 MB |
| Stephenson 2021 | 679 s, 2.90 GB | 13.6 s, 1438 MB | 7.4 s, 919 MB |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea6985f34203`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.