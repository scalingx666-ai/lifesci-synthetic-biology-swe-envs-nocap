# scalingX/lifesci-synthetic-biology-swe-envs-nocap

A domain-specific SWE-style RL environment dataset built from merged pull
requests of active, high-star Synthetic Biology & Genetic Circuits open-source repositories,
generated with the Repo2RLEnv pr_diff pipeline (Harbor task format).

Part of the lifesci-* multi-domain series. Published in parallel:
- Hugging Face: https://huggingface.co/datasets/scalingX/lifesci-synthetic-biology-swe-envs-nocap
- GitHub: https://github.com/scalingx666-ai/lifesci-synthetic-biology-swe-envs-nocap

## At a glance

- Build: expansion (no per-repo cap expansion)
- Target repositories: 37
- Repositories with tasks: 3
- Total tasks: 189
- Max tasks per repository: 171 (unlimited (no per-repo cap))
- Repositories with zero yield: 34 (kept in list, never faked)
- All targets: stars >= 50, pushed since 2023-01-01, not archived, noise-filtered

## Selection

Candidates came from domain GitHub topic/name/readme searches
(see selection_stats.json). Filter: active + stars >= 50 + non-archived +
non-fork + noise removed (awesome-lists / tutorials / courses / demos / etc.).
Top repositories by stars:
- thunlp/GNNPapers (16850 stars)
- PyO3/pyo3 (16325 stars)
- google-deepmind/alphafold (14939 stars)
- github/gh-ost (13646 stars)
- aimacode/aima-python (8873 stars)
- nomi-sec/PoC-in-GitHub (8196 stars)
- gepa-ai/gepa (7428 stars)
- guofei9987/scikit-opt (6727 stars)
- DEAP/deap (6462 stars)
- zouzhekang/YJYpaper (3631 stars)

Star buckets: {">=1000": 19, "500-999": 2, "200-499": 5, "100-199": 7, "50-99": 8}

## What a task is

Each task rewinds a merged PR to its base commit; the agent gets the PR title/
description (leak-stripped) and must edit the repo. A weighted diff-similarity
verifier compares its patch to the merged diff. Tasks ship a self-contained
python:3.12-slim inline Dockerfile. manifest.json / registry.json are added on
Hugging Face by repo2rlenv push.

## Files

- README.md, BREADTH_NOTES.md - card + build notes
- repo_list.txt - the domain target list
- dataset_stats.json - per-repo task counts
- selection_stats.json - selection funnel + star buckets
- zero_repos.txt - informational zero-yield list

## Caveats

- validate --deep --oracle = static structure + oracle integrity only, NOT
  a real graded Harbor reward (that needs an LLM judge key).
- Running tasks needs Docker (harbor run --env docker); generation/validation/
  publishing need neither Docker nor an LLM key.
- Hardcoded provider keys found in upstream PR diffs were redacted for public
  release. Licenses follow each source repository; generated with Repo2RLEnv.

## Snapshot scope

This release is a **partial snapshot** of an unfinished generation run.

- Generation-complete flag: generation_complete_expansion.flag - **ABSENT** (not faked)
- Bank progress at snapshot: **26225 / 100000** tasks (26.2%)
- This domain: **189** tasks from **3** repositories

See PARTIAL_SNAPSHOT.md for the full statement.
