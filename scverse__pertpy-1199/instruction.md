# Issue

**Title:** Apply biome 2.6 formatting to YAML and Markdown

## Description

biome 2.6.3 from #1195 also formats YAML and Markdown, which failed pre-commit on main.
This applies its formatting, with the YAML parsing to identical data, and excludes docs/tutorials.md because biome turns its front matter into a heading.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f22335a8256d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.