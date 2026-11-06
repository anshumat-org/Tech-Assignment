# QA Rubric — FullStack Assignment Scoring

**v1.1 — 2026-11-06** · Source of weights: FullStack Assignment brief (Assignments 01–05)
**Changelog:** v1.1 — added Assignments 03, 04, 05. v1.0 — first version.

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

## Assignment 03 — Mini Workflow Engine

| Area | Weight | Look for |
|---|---|---|
| Programming fundamentals | 20% | Correct CRUD, filters, search, pagination, activity recording; sound control flow and types |
| Database design and SQL | 20% | Schema, constraints, indexes, filtering and pagination in the database, update and activity in one transaction |
| API and backend design | 20% | The six endpoints, validation of status and priority, consistent errors (404, 400/422), concurrent-update handling |
| Code structure and maintainability | 20% | Routes, business logic and data access separated, reusable UI components, a new status (Blocked) is a small change |
| Testing and error handling | 10% | At least 5 meaningful tests including validation and an error case, transaction failure tested |
| UI usability | 10% | Loading, empty, success and error states, clear filters and status change |

## Assignment 04 — Passport Application & Tracking with DigiLocker

| Area | Weight | Look for |
|---|---|---|
| Data modelling and workflow / state machine | 20% | Entities per brief, one server-side state machine, invalid transitions rejected, roles per transition |
| Backend / API design and validation | 20% | Endpoints, validation, idempotent callback, consistent errors |
| Security, privacy, consent and auditability | 20% | Purpose-specific revocable consent, signed expiring state/nonce, ownership and role checks, redacted logs, audit events, no secrets or identity numbers in URLs or logs |
| DigiLocker adapter / integration simulation | 15% | Adapter interface, labelled mock, swappable provider, provider-down fallback route |
| Frontend and tracking experience | 15% | Checklist states, timeline with actor and time, consent card, simulation label, notifications |
| Tests, documentation and code quality | 10% | Tests for invalid transitions, duplicate callbacks, provider failure, access control. Retention and deletion explained |

Red flags: scraping government portals, asking for DigiLocker passwords or OTPs, presenting simulated data as real.

## Assignment 05 — Chat-First Inventory & Billing

| Area | Weight | Look for |
|---|---|---|
| Data model and inventory ledger | 15% | Movements as source of truth, balances consistent, product snapshots on orders, shop scoping |
| Order / billing correctness and transactions | 20% | Stock checks, discount and tax, unique numbers, DB transactions, idempotent confirm, no duplicate deduction |
| Bilingual intent handling and human confirmation | 20% | Hindi, English and Hinglish parsing, number phrases, ambiguity clarification, preview and explicit confirm, AI output validated |
| Daily stock and sales report accuracy | 20% | Stated formulas, shop timezone and day boundary, computed from persisted data, late return handling |
| Backend / API and shop-level access control | 10% | Shop and role checks on every query, API matches brief |
| Frontend usability and language experience | 5% | Language toggle, previews, tables, exports in both languages |
| Tests, error handling and documentation | 10% | At least 8 tests: bilingual parsing, ambiguity, report calculations, stock validation, duplicate retries, transaction failures |

Red flag: the AI computes or invents stock, prices, totals or report figures.

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
