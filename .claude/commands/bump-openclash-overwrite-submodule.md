---
name: bump-openclash-overwrite-submodule
description: Workflow command scaffold for bump-openclash-overwrite-submodule in Custom_OpenClash_Rules.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /bump-openclash-overwrite-submodule

Use this workflow when working on **bump-openclash-overwrite-submodule** in `Custom_OpenClash_Rules`.

## Goal

Updates the OpenClash_Overwrite submodule to a new commit, likely to pull in upstream changes.

## Common Files

- `overwrite/OpenClash_Overwrite`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update the submodule pointer for overwrite/OpenClash_Overwrite.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.