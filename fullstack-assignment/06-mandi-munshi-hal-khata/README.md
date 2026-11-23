# Assignment 06 — Mandi Munshi: Digital Hal Khata

**v1.0 — 2026-11-23**

| WH | Answer |
|---|---|
| What | A digital hal khata (running ledger) for a mandi commission-agent business. The owner and the munshi (clerk) record arrivals, sales, advances, deductions, payments and settlements per party |
| Why | Tests ledger design, money correctness, settlement logic, corrections without erasing history, and bilingual, low-friction data entry |
| Who | Mandi business owner, munshi (data entry), accountant or viewer (read-only). Parties are farmers/sellers and buyers/traders |
| How | TypeScript preferred. PostgreSQL preferred. Integer paise for all money. Hindi, English and Hinglish labels |
| When | 8–10 hours of effort. Review 30–45 minutes |
| Where | Runs locally. Synthetic data only |
| Which | Ledger and finance depth. Used after the Assignment 03 screen |

## Core idea

The paper hal khata is an append-only story of who owes whom. The digital version keeps that property: **entries are never edited or deleted, only reversed and re-posted**. Balances, daily cash book (rokad), outstanding lists and settlement slips (hisaab / patti) are all **derived from the ledger**, never typed in.

## Business context (synthetic, simplified)

| Term | Meaning in this brief |
|---|---|
| Aamad | Arrival of a farmer's lot (crop, quantity, unit) at the mandi |
| Bikri | Sale of a lot, in parts, to one or more buyers at a rate |
| Advance / peshgi | Money given to a farmer before or after the sale. Recoverable from the settlement |
| Deductions | Commission (arhat), mandi fee, labour (hamali), weighing (tulai), packing, other. Rates are configurable per crop or party |
| Hisaab / patti | Settlement of a farmer: sale proceeds minus deductions minus advances = net payable |
| Udhaar / baaki | A buyer's unpaid amount (credit sale) and its ageing |
| Rokad | The day's cash and bank book |

The brief is a deliberate simplification. If you assume a different rule from real practice, **state it in your README**.

## Evaluation weights

| Area | Weight |
|---|---|
| Ledger design and money correctness | 25% |
| Settlement (hisaab) and deduction logic | 20% |
| Corrections, reversals, audit trail and idempotency | 15% |
| Reports: party statement, rokad, outstanding ageing | 15% |
| Backend / API and role-based access | 10% |
| Frontend usability, bilingual and fast entry | 5% |
| Tests, error handling and documentation | 10% |

## Read next

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [design-system/README.md](design-system/README.md)
- [../developer-instructions.md](../developer-instructions.md) (mandatory for every assignment)
