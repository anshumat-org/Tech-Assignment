# Assignment 01 — Directives

**v1.0 — 2026-11-06**

| ✅ Do | ❌ Don't |
|---|---|
| Design the data model before coding | Start with the UI and bolt a schema on later |
| Persist the allocated question set | Regenerate questions on refresh |
| Make start and submit idempotent | Allow double attempts or double scoring |
| Hide answer keys and marks from candidate responses | Return `is_correct` or scoring rules to the browser |
| Snapshot what the candidate saw (text, options, marks) | Rely on live question rows after archive or edit |
| Validate every input and return consistent errors | Return raw database errors |
| Label psychometric output illustrative | Claim clinical validity or diagnosis |
| Test the six engineering scenarios | Test only the happy path |
| Document assumptions and trade-offs | Hide limitations |

## Deliverables

| Item | Format reference |
|---|---|
| Working app and GitHub repo | Meaningful commit history |
| ER diagram, schema, indexes, seed data | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 2 |
| HLD diagram | Section 1 |
| API documentation | Section 4 |
| Allocation algorithm and scoring explanation | In README or `docs/` |
| Five SQL queries and tests | Section 3 and 6 |
| README with setup, assumptions, trade-offs | Section 7 |
| Demo video or screenshots | Section 8 |

## Constraints
- TypeScript where practical. Justify major technology choices.
- Separate presentation, business logic, data access, external integrations.
- Runs locally. Docker optional.
- Synthetic data only.

## Technical discussion (30–45 min)
Expect to walk through architecture, schema and key queries, demo one end-to-end flow, discuss failure scenarios, and explain what changes before production.
