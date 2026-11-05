# QA Rubric — Assessment Scoring

**v1.0 — 2026-11-06** · Source of weights: OnRole assessment brief (Assignment 01 and 02)
**Changelog:** v1.0 — first version.

Score each area 0–5, then weight. Evidence (file and line, or command output) is required for every score.

| Score | Meaning |
|---|---|
| 0 | Missing |
| 1 | Present but broken or unusable |
| 2 | Partial, major gaps |
| 3 | Works, notable gaps |
| 4 | Solid, minor gaps |
| 5 | Strong, production-minded |

## Assignment 01 — Assessment & Intelligence Platform

| Area | Weight | Look for |
|---|---|---|
| Database design and SQL | 25% | Normalized schema, PK/FK/constraints, indexes with reasons, seed data, 5 queries incl. a CTE or window function, trade-offs explained |
| Backend architecture | 20% | Layer separation, input validation, consistent errors, idempotent start and submit, answer keys hidden from candidate responses |
| Question allocation engine | 20% | Blueprint quotas, no duplicates, persisted set, documented selection method, insufficient-pool handling, archived-question handling |
| Assessment execution and UI | 15% | Instructions, sections, timer, save and resume, single, multiple and Likert, deliberate submit, no double submit |
| Evaluation and scoring | 10% | Section totals, negative marking, reverse scoring, multi-dimension mapping, psychometric output labelled illustrative |
| Code quality and testing | 10% | Tests for critical flows and the 6 engineering scenarios, readable code, README |

## Assignment 02 — AI-Powered Daily Knowledge System

| Area | Weight | Look for |
|---|---|---|
| Database design and data modeling | 20% | Hierarchy, ordering, deletion, AI-output provenance, sync tables, indexes |
| System architecture and HLD | 15% | UI, logic, local store, remote store, AI and sync boundaries are clear |
| Frontend and editor implementation | 20% | Create, edit, delete, indent, outdent, reorder; node types; Markdown; date navigation |
| Local-first and sync architecture | 15% | IndexedDB, offline edit, queue, retry, duplicate-op handling, cursor or version, conflict explanation |
| AI integration and structured extraction | 15% | Provider interface, schema validation, timeout and failure handling, review before apply, original preserved, key server-side |
| Code quality and modularity | 10% | Structure, separation, naming |
| Testing and documentation | 5% | Tests, setup instructions, API and AI notes |

## Required-deliverable gate

| Item | Pass condition |
|---|---|
| Runs from clean clone | README commands work |
| HLD and ER diagram | Present, in the formats from `SUBMISSION_FORMATS.md` |
| Schema, indexes, API docs | Present |
| Tests | Exist and run |
| Demo | Video or screenshots |
| README | Assumptions, trade-offs, limitations, future work, AI usage disclosure |

## Verdict bands

| Weighted total | Verdict |
|---|---|
| 85–100 | Strong hire signal |
| 70–84 | Proceed to technical discussion |
| 50–69 | Borderline, discuss with hiring team |
| < 50 | Do not proceed |

The agent recommends only. The hiring team decides.
