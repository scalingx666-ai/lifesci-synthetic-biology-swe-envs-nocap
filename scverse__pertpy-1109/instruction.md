# Issue

**Title:** Make Milo differential abundance testing match R Milo

## Description

This aligns `Milo.da_nhoods` and `make_nhoods` with miloR 2.8.1, the current Bioconductor release: the edger solver uses the legacy quasi-likelihood fit that miloR pins, the pydeseq2 solver tests the same coefficient as the other solvers instead of falling back to the last level for contrasts without `-` and scaling continuous covariates by their range, and index cells now belong to their own neighbourhood.
The table compares pertpy with miloR on identical neighbourhood counts of the Stephenson COVID data (113 donors, 4307 neighbourhoods), plus one end-to-end run for the index cell change.
The remaining pydeseq2 differences come from the more conservative Wald test of DESeq2, e.g. 128 of the 144 Asymptomatic neighbourhoods that miloR calls draw at least 80% of their Asymptomatic cells from a single donor.

| Design | Solver | logFC ρ | logFC slope | p-value ρ | SpatialFDR < 0.1 (shared with miloR) | miloR |
|---|---|---|---|---|---|---|
| `~Status` | edger | 1.000 → 1.000 | 1.00 → 1.00 | 1.000 → 1.000 | 852 (802) → 803 (803) | 803 |
| `~Status` | pydeseq2 | 0.995 → 0.995 | 0.99 → 0.99 | 0.976 → 0.976 | 858 (743) → 858 (743) | 803 |
| `~Site+Status` | edger | 1.000 → 1.000 | 1.00 → 1.00 | 0.999 → 1.000 | 948 (914) → 926 (926) | 926 |
| `~Site+Status` | pydeseq2 | 0.994 → 0.994 | 0.88 → 0.88 | 0.965 → 0.965 | 915 (810) → 915 (810) | 926 |
| `~Site+COVID_severity`, `COVID_severityAsymptomatic` | edger | 1.000 → 1.000 | 1.00 → 1.00 | 0.998 → 1.000 | 129 (127) → 144 (144) | 144 |
| `~Site+COVID_severity`, `COVID_severityAsymptomatic` | pydeseq2 | 0.467 → 0.992 | 0.52 → 0.85 | 0.186 → 0.967 | 484 (12) → 1 (0) | 144 |
| `~Site+COVID_severity_continuous` | edger | 1.000 → 1.000 | 1.00 → 1.00 | 0.999 → 1.000 | 756 (734) → 747 (747) | 747 |
| `~Site+COVID_severity_continuous` | pydeseq2 | 0.998 → 0.998 | 6.55 → 1.31 | 0.987 → 0.987 | 795 (679) → 795 (679) | 747 |
| `~Status`, end to end on 15k cells with k = 30 | edger | | | | 196 → 211 | 218 to 225 over 3 seeds |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be2cd4196e34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.