# Review Checklist

Use this checklist before considering a change complete.

## Scope
- Does the change solve the requested problem and nothing unnecessary?
- Are touched files the right place for the change?
- If repeated friction was discovered, was it documented or automated at the right level?

## Quality
- Is the code consistent with existing patterns?
- Are names, boundaries, and responsibilities clear?
- Were dead paths or obsolete references removed when appropriate?
- Did the change avoid speculative abstraction and compatibility clutter?

## Documentation
- Were relevant docs updated if behavior, rules, or architecture changed?
- Do links and references still point to real files?
- Should the rationale for this change become a durable decision record?

## Verification
- Were relevant tests or checks run?
- Were manual verification steps used when automation was not enough?
- Are remaining risks or unverified areas explicitly called out?
