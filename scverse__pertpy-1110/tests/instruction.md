# Issue

**Title:** Make the pydeseq2 Milo solver reproduce R Milo

## Description

The pydeseq2 solver of `da_nhoods` now normalises like R Milo (library size times TMM factors, ported from edgeR), keeps the dispersions of pydeseq2 and tests with a likelihood ratio test instead of the Wald test, reporting the log fold change with the prior count of edgeR.
The Wald test and the floor of 0.5 that DESeq2 puts on fitted means lost almost all power in neighbourhoods a group barely populates, so the solver missed every Asymptomatic neighbourhood miloR calls on the tutorial data.
Follows #1109; the tables compare with miloR 2.8.1 on identical neighbourhood counts (Stephenson COVID data, 113 donors, 4307 neighbourhoods) and on a null and planted-depletion benchmark built from the same neighbourhoods.

| Design | logFC r with miloR | p-value ρ with miloR | SpatialFDR < 0.1 (shared with miloR) | miloR |
|---|---|---|---|---|
| `~Status` | 0.975 → 1.000 | 0.976 → 0.994 | 858 (743) → 817 (737) | 803 |
| `~Site+Status` | 0.959 → 0.992 | 0.965 → 0.982 | 915 (810) → 912 (846) | 926 |
| `~Site+COVID_severity`, `COVID_severityAsymptomatic` | 0.851 → 0.995 | 0.967 → 0.982 | 1 (0) → 72 (71) | 144 |
| `~Site+COVID_severity_continuous` | 0.745 → 0.994 | 0.987 → 0.991 | 795 (679) → 803 (726) | 747 |

| Benchmark | miloR | pydeseq2 before → after |
|---|---|---|
| Planted 90% depletion, 10 donors per group: recall | 0.50 | 0.31 → 0.48 |
| Same: false discovery proportion | 0.098 | 0.038 → 0.045 |
| Permuted labels, 113 donors: false calls per run | 14.8 | 3.2 → 3.8 |
| 10 against 10 healthy donors: false calls per run (20 runs) | 5.85 | 1.10 → 3.05 |
| 5 against 5 healthy donors: false calls per run (20 runs) | 11.45 | 0 → 6.30 |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7e0f024c92a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.