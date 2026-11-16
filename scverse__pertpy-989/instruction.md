# Issue

**Title:** scCODA: unify covariate index format across get_effect_df / summary / credible_effects

## Description

- \`get_effect_df\` and \`summary\` previously stripped \`[\`, \`]\`, and \`\"Condition\"\` from the \`Covariate\` index after building it from patsy column names, while \`credible_effects\` left the patsy-native format alone. The two views of the same model therefore disagreed (e.g. \`conditionT.Hpoly.Day3\` vs \`condition[T.Hpoly.Day3]\`), making it awkward to join their results.
- Drop the post-hoc rewrite so all three methods agree with each other and with the \`effect_df_{cov}\` keys already stored in \`varm\`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d50e6f0080a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.