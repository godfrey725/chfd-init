# Changelog

## 2026-03-19

### Changed
- strengthened generated root guidance in `AGENTS.md` and `CLAUDE.md`
- expanded `docs/index.md` and standards, plans, and architecture templates to better support durable planning, review, and operational guidance
- updated `SKILL.md`, `README.md`, and `references/usage.md` so the documented scaffold matches the generated bilingual template set
- moved the generated template source of truth to `templates/en/` and `templates/zh/`

### Added
- `templates/en/docs/decisions/README.md` and `templates/zh/docs/decisions/README.md` for concise ADR-style decision capture
- `templates/en/docs/runbooks/observability.md` and `templates/zh/docs/runbooks/observability.md` for logs, metrics, traces, dashboards, and alert guidance
- a full Chinese template tree under `templates/zh/`

### Notes
- safe-write behavior is unchanged: existing files are still skipped by default unless `--force` is used
- command prompt templates under `templates/en/.claude/commands/` and `templates/zh/.claude/commands/` were preserved
