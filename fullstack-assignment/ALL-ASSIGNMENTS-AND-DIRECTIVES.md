# FullStack Assignment — All Assignments and Directives

**v1.0 — 2026-11-06** · One-file summary of Assignments 01–05. Full detail lives in each assignment folder.

## 1. Overview

| # | Assignment | Focus | Effort | Review | Folder |
|---|---|---|---|---|---|
| 01 | Assessment & Intelligence Platform | Backend, DB design, SQL, allocation engine, scoring | 8–12 h | 30–45 min | [01](01-assessment-intelligence-platform/README.md) |
| 02 | AI-Powered Daily Knowledge System | Outliner UX, local-first, sync, AI extraction | 8–12 h | 30–45 min | [02](02-ai-daily-knowledge-system/README.md) |
| 03 | Mini Workflow Engine | Fundamentals, code quality, transactions, API design | 3–4 h | 20–30 min | [03](03-mini-workflow-engine/README.md) |
| 04 | Passport Application & Tracking (DigiLocker) | State machine, consent, adapters, security, audit | 6–8 h | 30–45 min | [04](04-passport-application-tracking/README.md) |
| 05 | Chat-First Inventory & Billing | Chat-to-action, ledger, bilingual UX, reports | 8–10 h | 30–45 min | [05](05-chat-first-inventory-billing/README.md) |

**Funnel:** start with 03, then 01 (backend/data), 02 (product/platform), 04 (integration/security) or 05 (commerce). Do not ask every applicant to complete all five.

## 2. Rules for every assignment

| Rule | Detail |
|---|---|
| Scope | Complete only the assignment selected for you |
| Window | 3 calendar days, then a technical discussion |
| Data | Synthetic only. No real personal data. No secrets in the repo |
| Stack | Any language. TypeScript preferred. Relational DB (PostgreSQL preferred, SQLite acceptable for 03) |
| Structure | Separate presentation, business logic, data access, integrations. No needless abstraction |
| Formats | Follow [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md) |

### Mandatory developer principles ([developer-instructions.md](developer-instructions.md))

| # | Principle | Rule |
|---|---|---|
| 1 | Human-instructed development | Driven by explicit human requirements. AI must not invent behaviour, change scope or make unrequested architecture decisions. Record assumptions |
| 2 | Human-approved changes | A human reviews and approves code, dependencies, schema and API changes, security logic and refactors. Run tests, explain changes |
| 3 | Codebase-first and reusable | Follow existing conventions. Reuse components, services and types. Avoid duplication, hacks and rewrites without reason |

Core principle: AI can assist implementation. Humans own the instructions, approval and quality.

## 3. Directives by assignment

### 01 — Assessment & Intelligence Platform

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

**Deliverables:** app and repo · ER diagram, schema, indexes, seed data · HLD · API docs · allocation and scoring explanation · five SQL queries and tests · README · demo.
**Constraints:** TypeScript where practical · layers separated · runs locally · synthetic data.
**Discussion (30–45 min):** architecture, schema and key queries, one end-to-end demo, failure scenarios, production changes.

### 02 — AI-Powered Daily Knowledge System

| ✅ Do | ❌ Don't |
|---|---|
| Write locally first, then sync | Block editing on network calls |
| Give every node a stable client-generated ID | Rely on server IDs for offline creates |
| Make sync operations idempotent, with retry | Apply the same operation twice |
| Use a cursor or version for pull | Re-download everything every time |
| Keep AI output separate from the original note | Overwrite the user's text with AI output |
| Show AI suggestions for review and edit before applying | Auto-apply extraction |
| Validate AI output against a schema. Handle timeout and failure | Trust raw model output |
| Keep AI keys on the server | Put keys in the frontend or repo |
| Show online/offline and sync state | Fail silently |
| Document the conflict strategy for edits and deletes | Leave conflicts undefined |

**Deliverables:** PWA or web app and repo · HLD · ER diagram, schema, indexes · API docs and AI notes · sitemap · setup and tests · offline edit and sync demo.
**Constraints:** TypeScript where practical · UI, logic, local store, remote store, AI and sync separated · runs locally · synthetic data.
**Discussion (30–45 min):** offline edit then reconnect, conflict handling, AI review flow, production changes.

### 03 — Mini Workflow Engine

| ✅ Do | ❌ Don't |
|---|---|
| Keep scope small and correct | Add auth, queues, microservices or caching |
| Write the task update and its activity row in one transaction | Log activity as an unrelated second write |
| Validate status and priority from one shared definition | Repeat allowed values in UI, API and DB separately |
| Filter, sort and paginate in the database | Load every task and filter in memory |
| Return clear errors (404, 400/422) in a consistent shape | Return raw database errors |
| Make adding a status a small change | Hard-code status strings across layers |
| Document assumptions and trade-offs | Hide limitations |

**Deliverables:** repo with setup · working app · schema or migration · one-page HLD · at least five meaningful tests (including validation and an error case) · README.
**Constraints:** any stack, TypeScript preferred · SQLite acceptable · layers separated · synthetic data.
**Discussion (20–30 min):** data model and constraints, likely failure mode, how you would test one part, a live **Blocked** status change.

### 04 — Passport Application & Tracking with DigiLocker

| ✅ Do | ❌ Don't |
|---|---|
| Put DigiLocker and tracking behind adapter interfaces | Call a provider directly from business logic |
| Label mock and simulated data in the UI and README | Present simulated status as real Passport Seva data |
| Enforce transitions in one server-side state machine | Trust the client to send a valid next status |
| Sign and expire the callback state/nonce. Make the callback idempotent | Accept a replayed or unsigned callback |
| Audit consent, document access, review decisions, status changes | Log document contents, identity numbers or tokens |
| Check ownership and role on every query | Rely on hidden UI buttons for access control |
| Store the minimum: references and metadata | Keep document copies or identity numbers you do not need |
| Offer another permitted upload route when the provider is down | Block the applicant completely |
| Use synthetic data only | Use real personal data or credentials |
| Never scrape government portals or ask for DigiLocker passwords or OTPs | Handle user authentication secrets in any form |

**Deliverables:** app and repo · HLD · ER diagram, schema, indexes, seed data · API docs · state machine diagram with roles per transition · consent, retention and deletion explanation · tests (invalid transitions, duplicate callbacks, provider failure, access control) · README · demo.
**Constraints:** TypeScript and PostgreSQL preferred · mock provider expected without sandbox credentials · layers separated · runs locally.
**Discussion (30–45 min):** state machine, consent capture and revocation, adapter replacement, data deliberately not persisted, tests for callbacks, failures and access.

### 05 — Chat-First Inventory & Billing

| ✅ Do | ❌ Don't |
|---|---|
| Treat model output as untrusted. Validate typed schemas and server-side rules | Execute whatever the model returns |
| Calculate stock, prices, tax, totals, payment status and reports deterministically | Let the AI invent or compute figures |
| Require confirmation for order, invoice, payment, refund and stock adjustment | Mutate data straight from a chat message |
| Use DB transactions and idempotency keys | Allow duplicate orders or stock deductions on retry |
| Keep an inventory ledger and derive balances from it | Overwrite a stock number with no history |
| Enforce shop and role scope on every query | Trust a shop ID sent by the client |
| Ask a focused clarification in the same language when ambiguous | Guess product, customer or quantity |
| Send the AI provider only what it needs | Send customer personal data unnecessarily |
| Provide a mock or deterministic parser and document the boundary | Make the app unusable without an AI key |
| Use synthetic data only | Use real shop or customer data |

**Deliverables:** chat-first app with Hindi, English and Hinglish examples · products, customers, orders, ledger, daily stock and sales reports · schema or migrations, HLD, API docs, README · at least 8 tests (bilingual parsing, ambiguity, report calculations, stock validation, duplicate retries, transaction failures) · demo (Hindi order, English order, stock report, sales report).
**Constraints:** TypeScript and PostgreSQL preferred · mock chat or LLM acceptable · layers separated · runs locally.
**Discussion (30–45 min):** message-to-persisted-action pipeline, ledger and report formulas, retry safety, live return or refund change.

## 4. Evaluation weights

Each assignment has its own area names and weights (each adds to 100%). See the "Evaluation weights" table in each README:
[01](01-assessment-intelligence-platform/README.md) · [02](02-ai-daily-knowledge-system/README.md) · [03](03-mini-workflow-engine/README.md) · [04](04-passport-application-tracking/README.md) · [05](05-chat-first-inventory-billing/README.md)

## 5. Open items

| Item | Status |
|---|---|
| [../qa/RUBRIC.md](../qa/RUBRIC.md) | Scores 01 and 02 only |
| [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md) | Says "Applies to Assignment 01 and Assignment 02" |
| `samples/` wireframes | Exist for 01 and 02 only |
