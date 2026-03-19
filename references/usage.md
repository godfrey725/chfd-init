# chfd-init Usage

## Invocation Examples

### Default
`chfd-init`

Effect:
- generates the `full` scaffold
- creates a richer agent-first repository harness
- skips existing files by default

### Explicit full
`chfd-init full`

Effect:
- generates the same complete harness as the default mode
- includes root guidance, docs structure, decisions, runbooks, and `.claude/commands/*`

### Minimal
`chfd-init minimal`

Effect:
- generates only the smallest viable harness
- keeps just enough structure for root guidance, standards entrypoints, and active-plan tracking

### Full without command prompts
`chfd-init full --no-commands`

Effect:
- generates the rich `full` docs scaffold
- omits `.claude/commands/plan.md`
- omits `.claude/commands/implement.md`
- omits `.claude/commands/verify.md`
- omits `.claude/commands/cleanup.md`

### Full without runbooks
`chfd-init full --no-runbooks`

Effect:
- generates the rich `full` scaffold
- omits `docs/runbooks/local-dev.md`
- omits `docs/runbooks/debugging.md`
- omits `docs/runbooks/observability.md`
- omits `docs/runbooks/verification.md`

### Minimal with force
`chfd-init minimal --force`

Effect:
- generates the minimal scaffold
- overwrites existing generated targets

### Minimal with no-runbooks
`chfd-init minimal --no-runbooks`

Effect:
- same result as plain `minimal`
- the flag has no additional effect because minimal mode does not generate runbooks

## What `full` Is For

Use `full` when you want a repository scaffold that is immediately usable for Claude Code collaboration.

The generated files establish:
- a read-first workflow through `AGENTS.md` and `docs/index.md`
- stable repository rules in `docs/standards/`
- architecture and boundary guidance in `docs/architecture/`
- plan and execution context under `docs/plans/`
- durable technical decision capture under `docs/decisions/`
- repeatable local-dev, debugging, observability, and verification procedures in `docs/runbooks/`
- reusable command prompts under `.claude/commands/`

The `full` scaffold is intentionally richer than a bare starter. It is meant to reduce repeated prompting and give agents explicit guidance for planning, implementation, verification, and documentation updates.

## What `minimal` Is For

Use `minimal` when you only want:
- root guidance files
- a standards entrypoint
- a lightweight golden-rules document
- a place to store active plans

Choose `minimal` if you want to add project documentation incrementally rather than generating the full CHFD docs tree upfront.

## Mode and Flag Matrix

| Input | Effect |
| --- | --- |
| `chfd-init` | Generate full scaffold |
| `chfd-init full` | Generate full scaffold |
| `chfd-init minimal` | Generate minimal scaffold |
| `chfd-init full --no-commands` | Omit `.claude/commands/*` |
| `chfd-init full --no-runbooks` | Omit `docs/runbooks/*` |
| `chfd-init minimal --force` | Overwrite existing generated targets |
| `chfd-init minimal --no-runbooks` | Same result as `minimal` |

## Expected Summary Output

Completion output should categorize results like:

- created: N
- skipped: N
- overwritten: N

It should also recommend a next reading order:
1. `AGENTS.md`
2. `docs/index.md`
3. relevant standards and architecture docs
4. active plans, decisions, or runbooks relevant to the current work

It should also make clear that generated does not mean ready. The scaffold is only a starter harness until the repository-specific guidance has been customized.

Minimum files to update first:
- `AGENTS.md`
- `CLAUDE.md`
- `docs/index.md`
- `docs/architecture/system-overview.md`
- `docs/architecture/domain-map.md`
- `docs/architecture/layering-rules.md`
- `docs/standards/golden-rules.md`

If the user generated `full`, recommend updating these before starting implementation:
- `docs/standards/coding-rules.md`
- `docs/standards/testing-rules.md`
- `docs/runbooks/local-dev.md`
- `docs/runbooks/verification.md`

## Notes

- Generation always targets the current working directory.
- Unknown modes or flags should fail clearly.
- Missing templates should stop generation with a precise error.
- Existing files without `--force` are skips, not failures.
- `full` is the default because it best expresses the CHFD workflow.
- `minimal` is intentionally lean and should not be expanded just to mirror `full`.
- Safe-write behavior is unchanged by the richer docs tree.
