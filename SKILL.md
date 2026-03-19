---
name: chfd-init
description: Use when initializing a Claude Code project with a reusable repository harness, starter docs, decisions, runbooks, and command templates for agent-first development.
---

# CHFD Init

## Overview

Initialize the current working directory with a CHFD (Claude Code Harness-First Development) starter scaffold.

Core principle: create an agent-readable repository harness first, then adapt it to the real project.

Templates live under `templates/` and are the source of truth. Generate into the current working directory only.

## When to Use

Use this skill when:
- starting a new Claude Code project
- standardizing an existing repo for agent-first development
- adding starter `AGENTS.md`, `CLAUDE.md`, `docs/`, and `.claude/commands/`
- you want safe, non-destructive initialization

Do not use this skill when:
- you need framework-specific app scaffolding
- you want package installation, CI setup, or source-code generation
- you want to modify a different directory than the current working directory

## Quick Reference

| Input | Effect |
| --- | --- |
| `chfd-init` | Generate the full scaffold |
| `chfd-init full` | Generate the full scaffold |
| `chfd-init minimal` | Generate the minimal scaffold |
| `chfd-init full --no-commands` | Omit `.claude/commands/*` |
| `chfd-init full --no-runbooks` | Omit `docs/runbooks/*` |
| `chfd-init minimal --force` | Overwrite existing generated targets |

## Modes and Flags

### Modes
- `full` (default)
- `minimal`

### Flags
- `--no-commands`
- `--no-runbooks`
- `--force`

`minimal --no-runbooks` is valid but has no additional effect because `minimal` does not generate runbooks.

## Generation Rules

Always operate on the current working directory. Do not infer or switch to another repository root.

### Full mode targets
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- `docs/standards/README.md`
- `docs/standards/golden-rules.md`
- `docs/standards/coding-rules.md`
- `docs/standards/testing-rules.md`
- `docs/standards/logging-rules.md`
- `docs/standards/review-checklist.md`
- `docs/plans/active/README.md`
- `docs/plans/completed/README.md`
- `docs/plans/tech-debt/README.md`
- `docs/architecture/README.md`
- `docs/architecture/system-overview.md`
- `docs/architecture/layering-rules.md`
- `docs/architecture/domain-map.md`
- `docs/decisions/README.md`
- `docs/runbooks/local-dev.md`
- `docs/runbooks/debugging.md`
- `docs/runbooks/observability.md`
- `docs/runbooks/verification.md`
- `.claude/commands/plan.md`
- `.claude/commands/implement.md`
- `.claude/commands/verify.md`
- `.claude/commands/cleanup.md`

### Minimal mode targets
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- `docs/standards/README.md`
- `docs/standards/golden-rules.md`
- `docs/plans/active/README.md`

### Subtraction rules
- `--no-commands`: remove `.claude/commands/*` from the target set
- `--no-runbooks`: remove `docs/runbooks/*` from the target set
- `--force`: allow overwrite of already existing generated targets

## Implementation Workflow

1. Parse arguments into mode and flags.
2. Default to `full` if no mode is supplied.
3. Reject unknown modes or flags with a clear error.
4. Resolve the target file list from mode plus flags.
5. For each target file, map it to the matching template under `templates/`.
6. Ensure the parent directory exists.
7. If the target file is missing, create it.
8. If the target file exists and `--force` is not set, skip it.
9. If the target file exists and `--force` is set, overwrite it.
10. Report created, skipped, and overwritten files.
11. Recommend next steps:
   - read `AGENTS.md`
   - read `docs/index.md`
   - adapt standards, decisions, and architecture docs to the real project

## Safe Write Policy

Default behavior is non-destructive.

Per target file:
1. create parent directories if needed
2. create missing files
3. skip existing files by default
4. overwrite only when `--force` is explicitly present

Never silently replace user-authored files.

## Error Handling

Fail clearly for:
- unknown mode
- unknown flag
- missing template file
- write permission failures

Non-error cases:
- existing file without `--force` → skip
- `minimal --no-runbooks` → valid, no extra effect

## Completion Output

At the end, report:
- created files
- skipped files
- overwritten files
- suggested reading order

## Common Mistakes

- Generating into the wrong directory: always use the current working directory only.
- Overwriting user files accidentally: do not replace existing files unless `--force` is present.
- Treating templates as examples only: templates are the source of truth for generated content.
- Adding framework-specific assumptions: keep v1 generic and starter-oriented.
