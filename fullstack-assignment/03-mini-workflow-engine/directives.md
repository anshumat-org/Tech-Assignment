# Assignment 03 — Directives

**v1.0 — 2026-11-06**

| ✅ Do | ❌ Don't |
|---|---|
| Keep scope small and correct | Add auth, queues, microservices or caching |
| Write the task update and its activity row in one transaction | Update a task and log activity as two unrelated writes |
| Validate status and priority from one shared definition | Repeat the allowed values in UI, API and DB separately |
| Filter, sort and paginate in the database | Load every task and filter in memory |
| Return clear errors (404, 400/422) with a consistent shape | Return raw database errors |
| Make adding a status a small change | Hard-code status strings across layers |
| Document assumptions and trade-offs | Hide limitations |

## Deliverables

| Item | Format reference |
|---|---|
| Git repo with setup instructions and meaningful commits | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7 |
| Working app | Demo video or screenshots, Section 8 |
| Schema or migration | Section 2 |
| One-page HLD | Section 1 |
| At least five meaningful tests, including validation and an error case | Section 6 |
| README with assumptions and trade-offs | Section 7 |

## Constraints
- Any language and framework. TypeScript preferred.
- Relational database. SQLite acceptable here.
- Separate presentation, business logic, data access.
- Synthetic data only.

## Technical discussion (20–30 min)
Walk through the data model and constraints, the most likely failure mode, how you would test one part of the code, and which files change if one requirement changes. Expect a live Blocked-status change.
