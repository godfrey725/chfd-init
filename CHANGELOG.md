# Changelog

## 2026-03-19

### Changed
- strengthened generated root guidance in `AGENTS.md` and `CLAUDE.md`
- expanded `docs/index.md` and standards, plans, and architecture templates to better support durable planning, review, and operational guidance
- updated `SKILL.md`, `README.md`, and `references/usage.md` so the documented scaffold matches the generated template set

### Added
- `templates/docs/decisions/README.md` for concise ADR-style decision capture
- `templates/docs/runbooks/observability.md` for logs, metrics, traces, dashboards, and alert guidance

### Notes
- safe-write behavior is unchanged: existing files are still skipped by default unless `--force` is used
- command prompt templates under `templates/.claude/commands/` were preserved
