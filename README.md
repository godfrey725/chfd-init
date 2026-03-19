# chfd-init

`chfd-init` is a global Claude Code skill for bootstrapping a project with a CHFD (Claude Code Harness-First Development) scaffold.

## Background

CHFD is a practical Claude Code development framework distilled from OpenAI's official Harness Engineering methodology and adapted for Claude Code's agent-first workflow.

The methodological reference comes from OpenAI's Harness Engineering article:
- English: https://openai.com/index/harness-engineering/
- Chinese: https://openai.com/zh-Hans-CN/index/harness-engineering/

This project does not copy OpenAI's harness model verbatim. Instead, it extracts the core ideas that are broadly transferable to Claude Code — explicit operating contracts, read-first repository guidance, durable plans, verification-before-completion, and reusable execution prompts — and turns them into a directly usable repository scaffold and initialization skill.

In other words, `chfd-init` is an opinionated Claude Code implementation of the same general harness-first philosophy: define the working environment, rules, docs structure, and execution flow upfront so agentic development becomes more reliable, repeatable, and easier to verify.

## Purpose

This skill turns the approved CHFD method into a reusable project initializer. It generates an agent-readable repository harness so Claude Code has explicit operating guidance before project-specific code and workflows are added.

In practice, the scaffold gives a repo:
- root operating contracts in `AGENTS.md` and `CLAUDE.md`
- a docs tree for standards, architecture, plans, decisions, and runbooks
- optional `.claude/commands/*` prompt contracts for planning, implementation, verification, and cleanup
- safe non-destructive initialization rules by default

## Install Location

- `~/.claude/skills/chfd-init/`

## Generated Modes

### `full`
Creates a complete starter harness for agent-first development.

Generated files include:
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- standards docs under `docs/standards/`
- plan tracking docs under `docs/plans/`
- architecture docs under `docs/architecture/`
- decision docs under `docs/decisions/`
- operational runbooks under `docs/runbooks/`
- `.claude/commands/plan.md`
- `.claude/commands/implement.md`
- `.claude/commands/verify.md`
- `.claude/commands/cleanup.md`

The generated `full` scaffold is meant to be directly usable, not just a placeholder. It establishes:
- a read-first workflow anchored by `docs/index.md`
- explicit expectations for planning non-trivial work
- documented architecture and boundary awareness
- a place to keep durable engineering decisions
- verification-before-completion rules
- documentation update expectations when behavior or workflows change

### `minimal`
Creates only the smallest viable harness:
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- `docs/standards/README.md`
- `docs/standards/golden-rules.md`
- `docs/plans/active/README.md`

Use `minimal` when you want a lightweight starting point without the fuller standards, architecture, decisions, runbook, and command-doc layers.

## Flags

- `--no-commands`: omit `.claude/commands/*`
- `--no-runbooks`: omit `docs/runbooks/*`
- `--force`: overwrite existing generated targets

## Safety Rules

- Generation applies to the current working directory only.
- Existing files are skipped by default.
- Only `--force` allows overwrite.
- Templates under `templates/` are the source of truth.
- The skill never silently replaces user-authored files.

## Recommended Next Steps After Generation

After running `chfd-init`, read in this order:
1. `AGENTS.md`
2. `docs/index.md`
3. relevant standards and architecture docs
4. active plans, decisions, or runbooks that apply to the current task

Then adapt the generated repository guidance to the real project instead of leaving the starter text unchanged.

## After Initialization: What You Must Customize Before Real Development

`chfd-init` creates a starter harness, not a fully configured project. Generation gives you the structure and default documents, but real development should start only after the generic starter text has been replaced with project-specific guidance.

### Must-update files first

Treat these as the minimum P0 set before doing substantial implementation work:
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- `docs/architecture/system-overview.md`
- `docs/architecture/domain-map.md`
- `docs/architecture/layering-rules.md`
- `docs/standards/golden-rules.md`

These files define the operating contract for agents and humans:
- what the project is and what it is for
- where code should live
- which dependencies and cross-layer calls are allowed
- how work should be planned, verified, and constrained

### Should-update before writing code in `full` mode

If you generated the `full` scaffold, complete these next:
- `docs/standards/coding-rules.md`
- `docs/standards/testing-rules.md`
- `docs/runbooks/local-dev.md`
- `docs/runbooks/verification.md`

These documents make the harness executable in practice by defining:
- code organization and naming rules
- test expectations and coverage boundaries
- local setup and startup steps
- the commands required to verify changes before completion

### Quick readiness checklist

Before treating the scaffold as ready for real work, confirm that the docs now answer these questions clearly:
- What is this repository for?
- What are the main modules or domains?
- Which layer should a change belong to?
- Which dependencies are allowed or forbidden?
- How do you run the project locally?
- What commands verify a change?
- Where do active plans and technical decisions live?

If those questions are still answered only by generic template text, the harness is initialized but not yet configured.

## Maintenance Notes

- Keep behavior rules in `SKILL.md`.
- Keep generated file bodies in `templates/`.
- Keep examples and mode matrix in `references/usage.md`.
- Keep `full` aligned with the richer CHFD workflow it generates.
- Keep `minimal` intentionally lean.
- Keep v1 framework-agnostic.
- Keep safe-write behavior unchanged unless there is an explicit design change.

## Extension Guidance

Possible future additions belong in follow-up versions, not v1:
- framework packs
- language overlays
- update/refresh mode
- scaffold validation mode
