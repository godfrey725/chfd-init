---
name: chfd-init
description: Use when initializing a Claude Code project with a reusable repository harness, starter docs, decisions, runbooks, and command templates for agent-first development.
---

# CHFD Init

## Overview

Initialize the current working directory with a CHFD (Claude Code Harness-First Development) starter scaffold.

Core principle: create an agent-readable repository harness first, then adapt it to the real project.

Templates live under `templates/<lang>/` and are the source of truth. Generate into the current working directory only.

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
| `chfd-init` | Prompt for language, then generate the full scaffold |
| `chfd-init full` | Prompt for language, then generate the full scaffold |
| `chfd-init full --lang zh` | Generate the full scaffold from the Chinese templates |
| `chfd-init minimal --lang en` | Generate the minimal scaffold from the English templates |
| `chfd-init full --no-commands` | Omit `.claude/commands/*` |
| `chfd-init full --no-runbooks` | Omit `docs/runbooks/*` |
| `chfd-init minimal --force` | Overwrite existing generated targets |

## Modes and Flags

### Modes
- `full` (default)
- `minimal`

### Flags
- `--lang en|zh`
- `--no-commands`
- `--no-runbooks`
- `--force`

If `--lang` is omitted, prompt the user to choose between `中文（推荐）` and `English` before generation begins.

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
- `--lang en|zh`: select the language-specific template tree
- `--no-commands`: remove `.claude/commands/*` from the target set
- `--no-runbooks`: remove `docs/runbooks/*` from the target set
- `--force`: allow overwrite of already existing generated targets

## Implementation Workflow

1. Parse arguments into mode and flags.
2. Default to `full` if no mode is supplied.
3. Resolve language from `--lang en|zh`, or prompt interactively when omitted.
4. Reject unknown modes or flags with a clear error.
5. Resolve the target file list from mode plus flags.
6. For each target file, map it to the matching template under `templates/<lang>/`.
7. Ensure the parent directory exists.
8. If the target file is missing, create it.
9. If the target file exists and `--force` is not set, skip it.
10. If the target file exists and `--force` is set, overwrite it.
11. Report created, skipped, and overwritten files.
12. Recommend next steps:
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
- invalid `--lang` value
- missing template file in the selected language tree
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

## Post-Generation Next Steps

Make clear that generation is only the start. `chfd-init` creates a starter harness, not a fully configured development environment.

Tell the user to customize the project-specific guidance before substantial implementation work begins.

Minimum files to update first:
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- `docs/architecture/system-overview.md`
- `docs/architecture/domain-map.md`
- `docs/architecture/layering-rules.md`
- `docs/standards/golden-rules.md`

If `full` mode was generated, also recommend updating:
- `docs/standards/coding-rules.md`
- `docs/standards/testing-rules.md`
- `docs/runbooks/local-dev.md`
- `docs/runbooks/verification.md`

Point users to `README.md` for the fuller explanation of what must be customized before real development.

## Common Mistakes

- Generating into the wrong directory: always use the current working directory only.
- Overwriting user files accidentally: do not replace existing files unless `--force` is present.
- Treating templates as examples only: templates are the source of truth for generated content.
- Adding framework-specific assumptions: keep v1 generic and starter-oriented.
