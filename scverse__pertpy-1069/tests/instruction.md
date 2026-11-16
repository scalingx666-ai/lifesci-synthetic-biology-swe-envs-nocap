# Issue

**Title:** Add mixed models to Milo differential abundance testing

## Description

A random intercept in the design switches `da_nhoods` to a negative binomial mixed model, so repeated measurements of the same donor, batch or timepoint are no longer treated as independent samples:

```python
milo.da_nhoods(mdata, design="~ Status + (1 | patient_id)")
```

The `(1 | variable)` syntax and the automatic switch on seeing a random effect both follow R Milo. Results gain `SE`, `tvalue`, one `<variable>_variance` per random intercept, `Dispersion`, `Logliklihood` and `Converged`.

Three bugs turned up along the way that are independent of this feature and are fixed here as well. `da_nhoods` dropped every column of a new result if any one of them was already present, so a second run with a solver reporting a different set of columns raised a `KeyError` on a column the first run never wrote. `subset_samples` reduced the design frame and then each solver reduced it again with a mask of the original length. And a random effect with a single level let a raw LAPACK error escape. Say the word if you would rather have those as their own pull request.

## Implementation

R Milo's GLMM is a custom pseudo-likelihood NB-GLMM (36 KB of R over 113 KB of C++), not lme4, so this is an independent implementation of the same method rather than a port: each iteration linearises the negative binomial likelihood into a working response, solves the weighted mixed model for the fixed effects and the BLUPs, and updates the variance components by Fisher scoring.

Neighbourhoods where a group has no cells are completely separated and have no finite estimate. R Milo screens these with `checkSeparation`; here they are reported as NaN and flagged unconverged rather than as an arbitrarily large fold change, which is what they degenerate to otherwise.

## Agreement with miloR 2.6.0

Same simulated data fitted by both implementations (20 donors x 8 samples, planted sigma = 1.0, dispersion = 0.15):

| | pertpy | miloR (HE) | miloR (Fisher) | truth |
|---|---|---|---|---|
| logFC vs miloR | r = 0.9999, mean abs diff 0.015 | - | - | - |
| t-value rank vs miloR | spearman 0.996 | - | - | - |
| dispersion | 0.157 | 0.785 | - | 0.15 |
| sigma | 0.974 | 0.904 | 621 (diverged) | 1.0 |
| converged | 40/40 | 0/40 | 0/40 | - |

Effect estimates agree with miloR essentially exactly, and so does the t-value ranking that decides which neighbourhoods are called significant. Standard errors come out about 2.5x smaller than miloR's, which traces to miloR's dispersion estimate landing ~5x above the planted value rather than to the standard error formula.

## Calibration

Agreement with another implementation says nothing about whether the p-values are correct, so they were checked against the null: data simulated with no condition effect, counting how often a neighbourhood is called significant at alpha = 0.05. 1500 replicates per scenario, so the Monte Carlo standard error is about 0.56 points.

Testing a coefficient that is constant within every level of a random intercept against the number of samples counts repeated measurements as independent observations, which is the pseudo-replication a mixed model exists to prevent. It matters most where there are few donors carrying many samples each:

| null scenario, condition constant within donor | df = n - p | between-within rule |
|---|---|---|
| 20 donors x 8 samples | 5.7% | 4.6% |
| 20 donors x 8 samples, sigma=1.0 | 5.9% | 4.3% |
| 10 donors x 4 samples | **8.5%** | **5.7%** |
| 8 donors x 6 samples | **9.2%** | **5.0%** |

With the rule in place every scenario tried, whether the condition varies within donors or between them, sits between 4.3% and 6.0% against a nominal 5%.

Two approximations were implemented for this and then removed after measuring them. A Kenward-Roger covariance adjustment changes the standard error by a factor of 1.0000, because a within-cluster contrast is orthogonal to the random intercept and a between-cluster one is already handled by the degrees of freedom. Satterthwaite degrees of freedom, with the dispersion treated as a variance component since it enters the variance matrix through its diagonal, reproduces the between-within rule to within one degree of freedom across balanced, unbalanced, partially confounded and small sample designs (138.0 against 139, 28.8 against 29, 18.0 against 18, 5.9 against 6) for identical type I error at ten times the runtime. The rule is kept; both are validation of it rather than replacements for it.

## On real data

The simulations above generate data from exactly the model the code assumes, which favours any correctly implemented estimator. So the same question was asked of a real graph: `pbmc68k_reduced`, eight donors each with their own composition, three samples per donor, and a condition that is a label on the donor with no effect of its own. Every neighbourhood called significant is a false positive.

| model | neighbourhoods | p<0.05 | SpatialFDR<0.1 | false positive rate |
|---|---|---|---|---|
| fixed effects only | 408 | 27 | 2 | 6.6% |
| random intercept | 407 | 11 | 0 | **2.7%** |

Aggregated over 8 seeds. Ignoring the donor structure calls false positives above the nominal rate and two survive multiple testing correction; the random intercept more than halves them and none survive.

The milo tutorial was also executed end to end against this branch, which runs the mixed model on `stephenson_2021` with `Site` as a random intercept: 4307 neighbourhoods, 6 of them with a group that has no cells and reported as NaN, 21 of the remaining 4301 not converged, and a site variance between 0.02 and 0.66.

## Degrees of freedom

The between-within rule was checked against the Satterthwaite approximation rather than taken on faith. Satterthwaite was implemented with the dispersion as an extra variance component, which is exact here because the dispersion enters the variance matrix through its diagonal so its derivative is the identity. It agrees with the rule across balanced, unbalanced, partially confounded and small sample designs:

| design | Satterthwaite | between-within |
|---|---|---|
| within donor, 20 x 8 | 138.0 | 139 |
| within donor, 10 x 4 | 28.8 | 29 |
| between donor, 20 x 8 | 18.0 | 18 |
| between donor, 10 x 4 | 8.0 | 8 |
| severely unbalanced clusters | 5.9 | 6 |

Type I error was identical in every case while the fit took 10x as long (8.5 to 81.5 ms), so the rule is kept and the Satterthwaite code is not.

## Performance

A neighbourhood is fitted one at a time, so a real run does this thousands of times. Solving against the Cholesky factor of the variance matrix instead of building its pseudoinverse, and taking the score and Fisher information traces in the space of random effect levels rather than of samples, is worth most of it. Timed in separate processes on 150 samples with 25 donors:

| | ms per fit |
|---|---|
| pseudoinverse | 1624 |
| Cholesky | 9.6 |
| Cholesky, products reused, warm start | 8.5 |
| the above with the adjusted profile likelihood dispersion | **13.4** |

The Cholesky rewrite matches the pseudoinverse version to 8e-15.

The dispersion is estimated by maximising the Cox-Reid adjusted profile likelihood rather than by solving a moment equation, iterated with the fit to consistency. A moment estimator needs to be told how many degrees of freedom the fit spent, and getting that wrong left the dispersion between 1% and 16% above the planted value depending on the size of the design; the adjusted profile likelihood holds it at -2% to -6% everywhere. Type I error is unchanged either way, but the dispersion is reported to the user, so its accuracy matters on its own.

## Notes

- Mixed models need `formulaic` for the fixed effects model matrix, which already ships in the `de` extra; `solver` and `model_contrasts` do not apply and the latter raises.
- The offset is the log library size rather than R Milo's `log(norm.factors)`, which omits library size.

The milo tutorial gained a section on this in scverse/pertpy-tutorials#71, which is merged, and the submodule pointer here picks it up, so nothing needs to follow. The notebook job of this pull request executes that section against this branch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca6b8914db6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.