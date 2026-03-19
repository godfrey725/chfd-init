# Testing Rules

## Test Strategy
- Add or update tests when behavior changes.
- Prefer tests that exercise real behavior over tests that only validate mocks.
- Keep tests focused on one behavior per case when practical.
- Reproduce bugs with a test before fixing them when possible.

## Verification
- Run the narrowest relevant test first.
- Re-run broader verification when shared behavior or interfaces change.
- Record what was verified and what could not be verified.
- If a failure mode matters repeatedly, turn it into a permanent regression check.

## Maintenance
- Remove obsolete tests when the behavior they covered no longer exists.
- Keep fixtures and helpers small and easy to understand.
- Prefer tests and commands that another agent can run without hidden setup.
