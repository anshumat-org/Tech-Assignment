# Assignment 05 — Directives

**v1.0 — 2026-11-06**

| ✅ Do | ❌ Don't |
|---|---|
| Treat model output as untrusted. Validate against typed schemas and server-side rules | Execute whatever the model returns |
| Calculate stock, prices, tax, totals, payment status and reports deterministically | Let the AI invent or compute figures |
| Require confirmation for order confirmation, invoice, payment, refund and stock adjustment | Mutate data straight from a chat message |
| Use DB transactions and idempotency keys for order, invoice, payment and stock | Allow duplicate orders or stock deductions on retry |
| Keep an inventory ledger and derive balances from it | Overwrite a stock number with no history |
| Enforce shop and role scope on every query | Trust a shop ID sent by the client |
| Ask a focused clarification in the same language when ambiguous | Guess product, customer or quantity |
| Send the AI provider only what it needs | Send customer personal data unnecessarily |
| Provide a mock or deterministic parser if no AI key is supplied, and document the boundary | Make the app unusable without an AI key |
| Use synthetic data only | Use real shop or customer data |

## Deliverables

| Item | Format reference |
|---|---|
| Working chat-first app with Hindi, English and Hinglish examples | Meaningful commit history |
| Product and customer management, orders, confirmation, ledger, daily stock and sales reports | |
| Schema or migrations, one-page HLD, API docs, README | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Sections 1, 2, 4, 7 |
| At least 8 tests: bilingual parsing, ambiguity, report calculations, stock validation, duplicate retries, transaction failures | Section 6 |
| Demo: one Hindi order, one English order, a daily stock report, a daily sales report | Section 8 |

## Constraints
- TypeScript preferred. PostgreSQL preferred.
- Mock chat or LLM integration is acceptable without credentials.
- Separate presentation, business logic, data access, external integrations.
- Runs locally.

## Technical discussion (30–45 min)
Walk through the pipeline from message to persisted action, the ledger and report formulas, retry safety, and the live return or refund change.
