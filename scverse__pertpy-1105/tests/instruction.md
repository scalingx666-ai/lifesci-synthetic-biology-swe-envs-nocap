# Issue

**Title:** fix(augur): use regression-appropriate scorers for regressor estimators

## Description

PR Checklist<!-- Many thanks for contributing to this project! -->

**PR Checklist**

<!-- Please fill in the appropriate checklist below (delete whatever is not relevant). These are the most common things requested on pull requests (PRs). -->

* [x] Referenced issue is linked
* [x] If you've fixed a bug or added code that should be tested, add tests!

**Description of changes**

<!-- Please state what you've changed and how it might affect the user. -->



`Augur` with a regressor estimator (e.g. `random_forest_regressor`) could crash during `predict()` with

`AttributeError: RandomForestRegressor has none of the following attributes: predict_proba.`

when the target had more than two distinct values (for example, multiple timepoints or a continuous outcome). In this case, the `multiclass` branch of `set_scorer` was selected and returned multiclass *classification* scorers, including scorers using `response_method="predict_proba"`, even though the estimator was a regressor.

The non-multiclass fallback also used a hardcoded `RandomForestClassifier | LogisticRegression` whitelist to select classification scorers. As a result, classifiers outside that whitelist could receive regression scorers.

`set_scorer` now checks whether the estimator is a regressor first, using scikit-learn's `is_regressor()`:

1. Regressors → regression scorers (`augur_score`, `r2`, `ccc`, `neg_mean_squared_error`, `explained_variance`), regardless of the `multiclass` argument.
2. Classifiers with `multiclass=True` → multiclass classification scorers (unchanged).
3. Other non-regressor estimators → binary classification scorers (unchanged scoring behavior, without the previous estimator whitelist).

This prevents regressor-based Augur runs from requesting class probabilities and ensures classifiers outside the previous hardcoded whitelist follow the classification-scoring path.

**Technical details**

<!-- Please state any technical details such as limitations, reasons for additional dependencies, benchmarks etc. -->

* `src/pertpy/tools/_augur.py`: reordered `set_scorer` so the `is_regressor(self.estimator)` branch is evaluated before the `multiclass` branch, and replaced the previous estimator-type ternary with the standard classification-scoring path.
* `tests/tools/test_augur.py`: added two regression tests for #655:

  * `test_regressor_scorer_with_more_than_two_labels` — verifies that `set_scorer(multiclass=True)` returns the regression scorer set for a random-forest regressor.
  * `test_regressor_cross_validation_with_four_timepoints` — end-to-end test using four numeric timepoints, verifying that cross-validation produces a finite `mean_ccc` and does not produce `mean_auc`.

The regression-specific scorer test ensures that a regressor with multiple target values is not assigned classification scorers. The end-to-end test verifies that the corrected scorer selection avoids the `predict_proba()` failure during cross-validation.

Environment: Windows, Python 3.14.6, scikit-learn 1.9.1. The mypy pre-commit hook and the full `hatch test` matrix could not run locally because `ete4` (via the `tcoda` extra) fails to build with Cython on Windows; this is pre-existing and unrelated to this change. CI will cover the supported test matrix.

**Additional context**

<!-- Add any other context or screenshots here. -->

`multiclass` is only meaningful for classifiers. A regressor with more than two distinct numeric target values remains a regression problem, so the estimator type must take precedence over the `multiclass` flag.

The documentation checklist item from the original template was removed because this is a bug fix with no API change requiring documentation updates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8abf85f90ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.