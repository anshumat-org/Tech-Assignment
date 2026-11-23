# Assignment 05 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 8–10 hours on transactional correctness, the ledger and deterministic reports, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

Steps total 9 h, inside the 8–10 h window.

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Schema: shops, users, products with aliases, customers, orders, invoices, payments, inventory movements and balances, chat, pending actions, audit | Migrations run from clean. Seed loads | 1 h |
| 2 | Inventory ledger and stock service | Balance equals the sum of movements. Stock check rejects oversell | 1 h |
| 3 | Order, invoice and payment services in transactions with idempotency keys | A retried confirm creates one order, one invoice and one stock deduction | 1.5 h |
| 4 | Reports: daily stock and daily sales, shop timezone and business-day boundary | Figures match hand calculation and the formulas in the brief | 1.5 h |
| 5 | Parser adapter: deterministic or mock, Hindi, English, Hinglish, number words and units | Parsing tests pass. Ambiguity returns a clarification | 1.25 h |
| 6 | Pipeline: pending actions, preview, confirm, execute. Role and shop scope | Nothing mutates before confirm. Pending actions expire | 1 h |
| 7 | UI: chat plus preview or report panel, language toggle, choice chips, export | Hindi order and English order work end to end | 1 h |
| 8 | Tests, docs, demo | Checklist C is complete | 0.75 h |

Ledger, transactions and reports first. Chat polish last.

## 2. Directions

| Topic | Direction |
|---|---|
| AI boundary | The assistant extracts typed fields. It never invents stock, prices, tax, totals, payment status or report figures. Treat model output as untrusted |
| Deterministic figures | Stock, totals, tax, payment status and reports come from persisted orders, payments and movements, not chat text or LLM arithmetic |
| Confirm | Explicit approval before order confirmation, invoice, payment, refund and stock adjustment |
| Ledger | Keep `inventory_movements`. Derive balances from it, and keep `inventory_balances` consistent with it |
| Transactions | Order, invoice, payment and stock changes in one DB transaction. Idempotency keys make retries safe |
| Pipeline | Follow the eight steps: understand, extract, resolve, validate, preview, confirm, execute, report |
| Ambiguity | Ask a focused clarification in the same language. Never guess product, customer or quantity |
| Language | Hindi, English and Hinglish in. Reply in the chosen or detected language. All labels, errors, reports and exports follow the toggle |
| Report formulas | Closing = opening + inward + returns-in − sold − returns-to-supplier − damage and other outward. Define gross sales, discounts, tax, net sales, refunds, collected and outstanding separately |
| Scope | Enforce shop and role on every query. Never trust a shop ID from the client |
| No AI key | Provide a mock or deterministic parser and document the boundary. The app must work without a key |
| Data to AI | Send only what the provider needs. No customer personal data unnecessarily |
| Limits | Typed input is required. Voice is optional. List skipped items under "Limitations" |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [design-system/README.md](design-system/README.md), [../developer-instructions.md](../developer-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 05 (not another one)
- [ ] Write down assumptions: business-day boundary, timezone, tax treatment, rounding, credit handling, pending-action expiry, branch scoping
- [ ] Choose stack: TypeScript and PostgreSQL preferred. Note any change and why
- [ ] Decide the parser: mock or deterministic, or a real provider behind an adapter. Document it
- [ ] Verify runtime, database and package manager work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Draft the ER diagram and a one-page HLD (Mermaid is fine)
- [ ] Sketch the report formulas with a worked example
- [ ] Plan the 8 steps above against your available hours
- [ ] Plan at least 8 tests: bilingual parsing, ambiguity, report calculations, stock validation, duplicate retries, transaction failures
- [ ] Plan synthetic seed data: products with Hindi and English aliases, similar names, customers, a few days of orders and movements
- [ ] Note the live follow-up: a return or refund flow, and a Hindi to English switch in one conversation

## 4. Checklist B — While developing

### Ledger and money
- [ ] Money handled in integer minor units or fixed decimals, never float
- [ ] Every stock change writes a movement with type, signed quantity, source, reason, actor
- [ ] Balances are derived from movements, or verified against them
- [ ] Oversell is rejected, such as 5 ordered with 3 available
- [ ] Order and invoice numbers are unique
- [ ] Payment methods cash, UPI, card and credit work, with outstanding credit tracked

### Transactions and idempotency
- [ ] Order confirm, invoice, payment and stock deduction commit together
- [ ] Forced failure mid-transaction rolls everything back
- [ ] Retried confirm after a timeout creates no duplicate order, invoice or deduction
- [ ] Pending actions are typed, validated and expire

### Chat pipeline
- [ ] Language and intent detected for order, product update, stock query, report, customer lookup, return
- [ ] Similar product names produce a choice, not a guess
- [ ] "pachaas" and "50" both become 50. A mismatched extraction is caught at preview
- [ ] Preview shows items, quantities, totals, stock impact and date range in the active language
- [ ] No mutation happens from a chat message without confirm
- [ ] Parser failure or no AI key still allows product search, order entry and reports

### Reports
- [ ] Daily stock report: opening, inward, sold, returns, adjustments, closing, low stock
- [ ] Daily sales report: gross sales, discounts, tax, net sales, order count, average order value, top products, payment split, refunds, outstanding dues
- [ ] Uses shop timezone and an explicit day boundary
- [ ] Calculated from the database, not the transcript
- [ ] A late return corrects reports and leaves an audit trail
- [ ] Hindi and English headings, labels, filters and exports

### API and security
- [ ] Shop and role come from the session, not the request
- [ ] Inputs validated with schemas. Consistent errors in the active language
- [ ] Audit event for confirms, refunds and adjustments
- [ ] No secrets or real shop or customer data in code, logs or seed data

### UI
- [ ] Hindi / English toggle changes every label, error, confirmation and export. Devanagari renders correctly
- [ ] Preview card has explicit Confirm and Cancel and says what will change
- [ ] Choice chips for ambiguous product or customer
- [ ] Low stock marked with text and an icon, not colour alone
- [ ] Works at phone width

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go (you must disclose it)

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, migrate, seed, start, test. All work
- [ ] At least 8 tests pass, covering bilingual parsing, ambiguity, report calculations, stock validation, duplicate retries and transaction failures
- [ ] Reports reconcile to ledger, order and payment rows
- [ ] Rehearse the engineering scenarios: similar names, 5 ordered with 3 available, "pachaas" misparse, confirm retry, late return, two branches, AI provider down
- [ ] Live-change rehearsal: add a return or refund so order, payment, restock and reports stay consistent and audited. Switch Hindi to English mid-conversation without losing context

### Deliverables
- [ ] Working chat-first app with Hindi, English and Hinglish examples
- [ ] Schema or migrations, one-page HLD, API docs ([SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Sections 1, 2, 4)
- [ ] `docs/testing.md` (Section 6)
- [ ] Demo: one Hindi order, one English order, a daily stock report, a daily sales report (Section 8)
- [ ] README contains: overview, quick start, assumptions, day-boundary and timezone rule, live vs snapshot report explanation, parser boundary, trade-offs, limitations, future work, AI usage disclosure (Section 7)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk through the pipeline from message to persisted action
- [ ] Can explain the ledger and report formulas
- [ ] Can explain retry safety
- [ ] Can do the live return or refund change
- [ ] Can identify AI-generated code and explain it

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Executing what the model returned | Validate against typed schemas and server rules |
| LLM computes totals or report figures | Deterministic services and SQL |
| Mutating on a chat message | Pending action, preview, explicit confirm |
| Overwriting a stock number | Append ledger movements, derive balance |
| Retry creates a second order or deduction | Idempotency key and one transaction |
| Guessing between similar products | Clarify with choice chips in the same language |
| Reports built from the transcript | Build from orders, payments and movements |
| Shop ID taken from the client | Shop and role from the session |
| App breaks with no AI key | Deterministic or mock parser |
| Only English strings translated | Labels, errors, reports and exports all bilingual |
