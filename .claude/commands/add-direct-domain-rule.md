---
name: add-direct-domain-rule
description: Workflow command scaffold for add-direct-domain-rule in Custom_OpenClash_Rules.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-direct-domain-rule

Use this workflow when working on **add-direct-domain-rule** in `Custom_OpenClash_Rules`.

## Goal

Adds a new domain to the direct routing rules, then regenerates all derived rule files in multiple formats for OpenClash.

## Common Files

- `rule/Custom_Direct.list`
- `rule/Custom_Direct_Domain.yaml`
- `rule/Custom_Direct_Classical.yaml`
- `rule/Custom_Direct_Domain.mrs`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit rule/Custom_Direct.list to add the new domain.
- Auto-generate rule/Custom_Direct_Domain.yaml from rule/Custom_Direct.list.
- Auto-generate rule/Custom_Direct_Classical.yaml from rule/Custom_Direct.list.
- Auto-generate rule/Custom_Direct_Domain.mrs from rule/Custom_Direct_Domain.yaml.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.