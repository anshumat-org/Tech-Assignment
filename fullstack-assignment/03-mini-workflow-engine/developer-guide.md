# Assignment 03 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 3–4 hours on correctness and structure, and stay ready for the live Blocked-status change |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

Steps total 3.5 h, inside the 3–4 h window.

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Schema: `tasks`, `task_activities`, constraints, indexes. One shared definition of status and priority | Migration runs from clean. Bad status or priority is rejected | 0.5 h |
| 2 | Service layer: create, update, delete in one transaction with the activity row | Task and activity commit together or not at all | 0.75 h |
| 3 | API: the six endpoints, validation, consistent errors, DB-side filter, search and pagination | 404 and 400/422 return a consistent shape | 0.75 h |
| 4 | UI: list with filters and search, one reusable form, detail with timeline | Loading, empty, success and error states all exist. Delete asks to confirm | 1 h |
| 5 | Tests, README answers to the engineering depth checks, demo | Checklist C is complete | 0.5 h |

Keep scope small. Correct beats big.

## 2. Directions

| Topic | Direction |
|---|---|
| Scope | Do not add auth, queues, microservices or caching |
| Transactions | The task write and its activity row go in one transaction |
| One definition | Status and priority values come from one shared definition used by UI, API and DB |
| Extensibility | Adding a status (the live **Blocked** change) must touch few files: definition, DB representation, UI, tests |
| Filtering | Filter, sort and paginate in the database, not in memory |
| Errors | 404 for a missing task, 400/422 for bad input, one error shape. No raw database errors |
| Structure | Separate routes/controllers, business logic and data access |
| UI | Reusable task form for create and edit. Status and priority chips carry text, not colour alone |
| Concurrency | Decide and document what happens on near-simultaneous updates |
| Database | SQLite is acceptable, PostgreSQL preferred. Justify indexes |
| Scope notes | List anything skipped under "Limitations" in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [design-system/README.md](design-system/README.md), [../developer-instructions.md](../developer-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 03 (not another one)
- [ ] Write down assumptions: concurrency approach, what delete does to history, pagination style
- [ ] Choose stack. Any language and framework, TypeScript preferred. Note why
- [ ] Verify runtime, database and package manager work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Sketch the two tables and a one-page HLD (Mermaid is fine)
- [ ] Read the six engineering depth checks (section D) and note your answers early
- [ ] Plan the 5 steps above against your available hours
- [ ] Plan at least five tests, including validation and an error case
- [ ] Plan a few synthetic tasks for seed data

## 4. Checklist B — While developing

### Data and transactions
- [ ] Constraints enforce allowed status and priority values
- [ ] Indexes match your filter and search queries, with a reason
- [ ] Create, edit, delete and status change each write an activity row
- [ ] Task update and activity insert are in one transaction. A forced failure rolls both back
- [ ] `updated_at` changes on edit

### API
- [ ] Six endpoints work: create, list, get, patch, delete, activities
- [ ] List supports status filter, priority filter, text search and pagination in the database
- [ ] Update or fetch of a missing task returns a clear 404
- [ ] Invalid input returns 400/422 with useful messages in one consistent shape
- [ ] Status and priority are validated from the shared definition

### Structure
- [ ] Routes, business logic and data access are separate
- [ ] No duplicated task form or list logic in the UI
- [ ] No hard-coded status strings scattered across layers
- [ ] Types or schemas for request and response data

### UI
- [ ] Filters and search sit in one row, with a clear-filters action
- [ ] Task detail shows fields on top and a chronological timeline below
- [ ] Loading, empty, success and error states are all designed
- [ ] Confirm before delete
- [ ] Chips show text, not colour alone

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go (you must disclose it)

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, migrate, seed, start, test. All work
- [ ] At least five meaningful tests pass, including validation and an error case
- [ ] A test proves the transaction rollback, or you explain how you would test it
- [ ] Dry run of the live follow-up: add a **Blocked** status and confirm it is a small change across UI, API validation, DB, activity history and tests, then revert or keep it as you prefer

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits ([SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7)
- [ ] Working app with demo video or screenshots (Section 8)
- [ ] Schema or migration with keys, constraints and index justification (Section 2)
- [ ] One-page HLD (Section 1)
- [ ] README answers all six engineering depth checks: missing task update, transaction for update plus activity, where filtering happens, status and priority validation, concurrent updates, which operations need transactions and how to test failure
- [ ] README contains: overview, quick start, assumptions, trade-offs, limitations, future work, AI usage disclosure

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (20–30 min)
- [ ] Can walk through the data model and constraints
- [ ] Can name the most likely failure mode
- [ ] Can explain how you would test one part of the code
- [ ] Can say which files change if one requirement changes
- [ ] Ready for the live Blocked-status change
- [ ] Can identify AI-generated code and explain it

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Update and activity log as two separate writes | One transaction |
| Status strings repeated in UI, API and DB | One shared definition |
| Loading all tasks and filtering in memory | Filter, sort, paginate in SQL |
| Raw database errors returned | Map to 404 and 400/422 with one shape |
| Adding auth, caching or queues | Stay in scope |
| Two copies of the task form | One reusable form for create and edit |
| Only the happy path tested | Add validation and error-case tests |
| Colour-only status chips | Text plus colour |
