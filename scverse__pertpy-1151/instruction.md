# Issue

**Title:** Include the diagonal in euclidean within-group mean distances

## Description

The numba euclidean kernel averaged within-group distances over n(n-1) ordered pairs while the precomputed path, sklearn's pairwise_distances(...).mean() used for all other metrics, and scperturb average over n^2 including the zero diagonal.
`Distance("edistance")(X, Y)` and `pairwise` therefore disagreed with `DistanceTest` and `onesided_distances(bootstrap=True)` on the same cells (0.047 vs 0.171 in a 40 vs 60 cell example); euclidean e-distance, mean_pairwise and DistanceSpace values change to the n^2 convention and all paths now agree.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27dae8b564c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.