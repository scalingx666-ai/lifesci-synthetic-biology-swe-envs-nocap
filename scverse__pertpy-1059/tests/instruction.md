# Issue

**Title:** Align dataset download progress

## Description

**Description of changes**

Left-align output filenames in a 40-character field so that progress bars for sequential dataset downloads start at the same position.

- Before: Progress bars start at different positions depending on the filename length.
   <img width="764" height="50" alt="Screenshot 2026-07-29 at 09 00 00" src="https://github.com/user-attachments/assets/9772d4f0-4987-4fee-807b-1059b73baf0e" />

- After: The output filenames use a minimum width of 40 characters, aligning the progress bars, percentages, and remaining-time columns.
   <img width="766" height="49" alt="Screenshot 2026-07-29 at 08 59 42" src="https://github.com/user-attachments/assets/830ca6e9-f246-4c1a-8148-0e14ce2e718d" />

**Technical details**

The longest output filename currently defined in `_datasets.py` is 38 characters (which is "schraivogel_2020_tap_screen_chr11.h5ad").
The 40-character field is a minimum width, so longer filenames will still be displayed in full rather than truncated.

Validation:
- `uv run pre-commit run --files pertpy/data/_dataloader.py`
- `git diff --check`

**Additional context**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6de6b184ac12`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.