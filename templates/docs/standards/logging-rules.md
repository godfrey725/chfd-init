# Logging Rules

## Purpose
Logging should help diagnose behavior without overwhelming normal development workflows.

## Rules
- Log at system boundaries, important state transitions, and failures.
- Prefer structured, searchable messages when the stack supports them.
- Do not log secrets, credentials, or sensitive personal data.
- Avoid noisy logs in hot paths unless they are explicitly temporary.

## Operational Guidance
- Include enough context to trace what happened.
- Remove temporary debug logging before finishing work unless it is intentionally retained.
- Keep log wording consistent so operators can search reliably.
