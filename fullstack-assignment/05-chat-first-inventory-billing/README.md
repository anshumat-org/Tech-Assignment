# Assignment 05 — Chat-First Inventory & Billing Platform

**v1.0 — 2026-11-06**

| WH | Answer |
|---|---|
| What | An inventory and billing app for a small retailer, driven by chat in Hindi, English or Hinglish |
| Why | Tests chat-to-action design, transactional correctness, inventory ledger, deterministic reporting and bilingual UX |
| Who | A shop owner (and staff by role) managing daily operations |
| How | TypeScript preferred. PostgreSQL preferred. Mock or deterministic parser adapter if no AI key is supplied |
| When | 8–10 hours of effort. Review 30–45 minutes |
| Where | Runs locally. Synthetic data only |
| Which | Commerce depth. Used after the Assignment 03 screen |

## Core idea

The assistant converts instructions into structured actions, reads figures from the database, and **previews consequential changes before the owner confirms**. The AI never invents stock, prices, tax, totals, payment status or report figures.

## Evaluation weights

| Area | Weight |
|---|---|
| Data model and inventory ledger | 15% |
| Order / billing correctness and transactions | 20% |
| Bilingual intent handling and human confirmation | 20% |
| Daily stock and sales report accuracy | 20% |
| Backend / API and shop-level access control | 10% |
| Frontend usability and language experience | 5% |
| Tests, error handling and documentation | 10% |

## Read next

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [design-system/README.md](design-system/README.md)
- [../developer-instructions.md](../developer-instructions.md) (mandatory for every assignment)
