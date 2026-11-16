# Issue

**Title:** Make Augur faithful to R Augur and twice as fast

## Description

Augur scores each cross-validation fold in one pass over a forest fitted tree by tree with scikit-learn's own seeds, which keeps every AUC, accuracy and importance bit for bit identical to main on seeded runs while the tutorial job drops from 14.2 to 6.9 min in CI. Comparing against neurorestore/Augur 1.0.3 also fixed the label encoding after filtering (binary precision, recall and F1 were silently NaN for the 48h comparison and b, z and p-values of the differential prioritization could be assigned to the wrong cell type), the positive class, `min_cells` semantics, the 1000-feature thresholds, regressor folds, per-cell score assignment, and the reproducibility of unseeded runs and of the differential prioritization draws; the regenerated tutorial is scverse/pertpy-tutorials#81.

Performance of `predict` with 50 subsamples (default) and 100 permuted subsamples (permute), 4 threads on the same 4 cores of a machine at load average above 100, peak RSS of the main process plus its largest worker:

| Dataset | main default / permute | main RSS | this PR default / permute | this PR RSS |
|---|---|---|---|---|
| sc_sim (600 cells, 3 types, 15,697 genes) | 14 s / 27 s | 2.3 GB | 9 s / 13 s | 1.2 GB |
| Bhattacherjee 15d (9,599 cells, 8 types, 18,469 genes) | 36 s / 67 s | 4.7 GB | 22 s / 37 s | 4.2 GB |
| Bhattacherjee 48h (6,313 cells, 8 types, 18,469 genes) | 37 s / 60 s | 4.0 GB | 24 s / 37 s | 3.6 GB |
| Kang 2018 (24,541 cells, 7 types, 3,000 genes) | 29 s / 52 s | 2.0 GB | 19 s / 29 s | 1.0 GB |
| Augur tutorial, CI `test (augur.ipynb)` job | 14.2 min | | 6.9 and 8.9 min on two runs | |

Accuracy against R Augur (`calculate_auc`, `n_subsamples = 50`, `select_var = TRUE`, R 4.5.3, randomForest 4.7.1.2). Spearman is over the per-cell-type mean AUCs, the AUC offset is the mean over cell types with the largest difference in standard errors, precision and recall are mean absolute differences of the per-cell-type means:

| Dataset | main AUC rank Spearman | main AUC minus R | main precision / recall diff | this PR AUC rank Spearman | this PR AUC minus R | this PR precision / recall diff |
|---|---|---|---|---|---|---|
| sc_sim | 1.00 | +0.052 (max z 5.9) | 0.121 / 0.187 | 1.00 | +0.052 (max z 4.9) | 0.100 / 0.089 |
| Kang 2018 | 0.96 | +0.042 (max z 3.7) | 0.073 / 0.115 | 0.96 | +0.042 (max z 3.6) | 0.072 / 0.045 |

The variance-based gene selection agrees with R to 99.6 to 99.7% (Jaccard) on sc_sim. The AUC offset is the classifier, not the pipeline: on one identical 40-cell subsample and fold assignment scikit-learn's forest gives 0.919 and R's randomForest 0.883 at `mtry = 2`, while both give 0.94 to 0.95 at `mtry = sqrt(p)`, because randomForest stops a node when the drawn features cannot split it and scikit-learn keeps searching. The ranking of cell types, which is Augur's output, agrees. Two differences remain documented rather than closed: that split search has no scikit-learn switch, and pertpy reports impurity importance where R reports permutation importance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eec86bc2b7ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.