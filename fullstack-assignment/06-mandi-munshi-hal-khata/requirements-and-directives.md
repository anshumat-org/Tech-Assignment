# Assignment 06 — Requirements & Directives

**v1.0 — 2026-11-23**

## Part 1 — Requirements

### A. Core workflows

| Workflow | Requirement |
|---|---|
| Parties | Create farmers and buyers. Name, village or shop, phone (optional), type, opening balance with Dr/Cr side. Search by Hindi or English name |
| Aamad (lot arrival) | Record a lot: party, crop, quantity, unit (kg, quintal, bag, crate), date. A lot has a status: open, partly sold, sold, settled |
| Bikri (sale) | Sell part or all of a lot to a buyer: quantity, rate, amount, cash or credit. Cannot sell more than the remaining lot quantity |
| Advance | Give money to a farmer, by cash, UPI or bank. Optionally linked to a lot |
| Deductions | Configurable rates per crop or party: commission %, mandi fee %, hamali and tulai per unit, other flat. Applied at settlement, shown line by line |
| Receipts and payments | Receive from a buyer, pay a farmer. Allocate to specific sales or lots, or keep on account |
| Hisaab / patti | Settle a farmer's lot or period: total sales − deductions − advances recovered = net payable. Preview, then confirm to post. Printable in Hindi or English |
| Corrections | Wrong rate, wrong quantity, wrong party. Fix by **reversal plus re-posting** with a reason. Nothing is edited in place |
| Reports | Party statement (khata), daily rokad, outstanding and ageing, lot-wise profit of commission |

### B. Ledger rules

| Rule | Expectation |
|---|---|
| Money type | Integer paise or a decimal type. Never floating point. Quantities as decimals with a stated precision |
| Double entry | Every posting has balanced debit and credit lines. A party balance is the sum of its lines |
| Append only | Posted entries are immutable. Enforce in the database or service layer, and say how |
| Reversal | A reversal links to the original, mirrors its lines and carries a reason and actor |
| Rounding | State the rounding rule for percentages (for example half-up to the paisa) and where rounding differences go |
| Dates | Entry date (business date) is separate from created-at (system time). Define the business-day boundary and timezone |
| Closed periods | Decide what happens when someone posts into a settled lot or a closed day. Document it |

### C. Reports

| Report | Content |
|---|---|
| Party statement | Opening, each entry (date, narration, Dr, Cr, running balance), closing. Date range filter. Matches the sum of ledger lines exactly |
| Daily rokad | Opening cash and bank, receipts, payments, closing. By mode. Reconciles to the ledger |
| Outstanding | Buyers' baaki and farmers' payable, with ageing buckets (0–7, 8–30, 31–60, 60+ days). Oldest unpaid first |
| Lot summary | Quantity in, sold, remaining. Sale value, deductions, commission earned, advances recovered, net payable |
| Export | CSV and a printable summary in Hindi or English |

### D. Database (suggested)

| Entity | Purpose |
|---|---|
| businesses / users | Tenancy, roles (owner, munshi, viewer), language, timezone |
| parties | Type (farmer, buyer), names in both scripts, opening balance |
| lots | Party, crop, quantity in, unit, status, arrival date |
| sales | Lot, buyer, quantity, rate, amount, payment mode |
| accounts | Chart of accounts: party control, cash, bank, commission income, fees payable |
| journal_entries / journal_lines | Entry date, narration, source reference, balanced lines, reversal link |
| settlements | Lot or period, computed lines, status (draft, posted, reversed) |
| deduction_rules | Crop or party scope, type, rate, effective-from date |
| idempotency_keys | Safe retries for every posting endpoint |
| audit_events | Actor, action, entity, reason, before/after reference, timestamp |

### E. API scope (adjustable if documented)

| Method | Endpoint |
|---|---|
| POST / GET | /parties · /parties/{id}/statement?from=&to= |
| POST | /lots · /lots/{id}/sales |
| POST | /advances · /receipts · /payments |
| POST | /settlements/preview · /settlements/{id}/post |
| POST | /entries/{id}/reverse |
| GET | /reports/rokad?date= · /reports/outstanding · /lots/{id}/summary |
| GET | /reports/{id}/export?format=csv\|pdf |

### F. Settlement logic

- Net payable = Σ sale amounts − Σ deductions − Σ advances recovered ± adjustments.
- Show every deduction as its own line with the rate and base used.
- If advances exceed the proceeds, the farmer owes the business. Show it, carry it forward, never hide it.
- Settlement preview and posted settlement must give the same figures for the same inputs.
- Define what happens if a sale is corrected after the settlement is posted.

### G. Engineering scenarios to address

- The munshi enters 4,500 kg but meant 450 kg. How is it caught or corrected, and what does the farmer's statement show afterwards?
- A rate was wrong on a sale already included in a posted settlement. How do the buyer's khata, the farmer's hisaab and the rokad stay consistent?
- A receipt request is retried after a timeout. How do you prevent a double credit?
- Two munshis post to the same lot at the same time and together exceed its quantity. What stops it?
- Commission is 2.5% of ₹1,234.56. Where does rounding go, and do the lines still balance?
- A buyer pays ₹10,000 against four open sales. How is it allocated, and can the owner override?
- Deduction rates change mid-season. Which rate applies to a sale made before the change?
- The phone loses network in the mandi. What do you do, and what do you not promise?

### H. Live follow-up
Reverse a posted settlement after a sale rate correction and re-post it. Show the farmer's statement before and after, the buyer's outstanding, and the day's rokad, all still balanced and fully auditable. Switch the interface from Hindi to English mid-session.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Store money as integer paise or a decimal type | Use floating point for money |
| Post balanced journal entries in a DB transaction | Update a balance column directly |
| Correct by reversal and re-posting with reason and actor | Edit or delete a posted entry |
| Derive every report from ledger lines | Keep separately typed totals that can drift |
| Use idempotency keys on every posting endpoint | Allow double credits or double deductions on retry |
| Lock or constrain concurrent sales against a lot | Let two clerks oversell a lot |
| Enforce business and role scope on every query | Trust a business ID or role sent by the client |
| Preview settlements and require confirmation before posting | Post a settlement from a single click with no preview |
| Show Hindi and English labels, Devanagari numerals optional | Hard-code one language into reports |
| State rounding, day boundary and closed-period rules in the README | Leave them implicit |
| Use synthetic data only | Use real farmer, trader or business data |

### Deliverables

| Item | Format reference |
|---|---|
| Working app: parties, lots, sales, advances, receipts, payments, settlement, reversal | Meaningful commit history |
| Party statement, daily rokad, outstanding ageing, lot summary | |
| Schema or migrations with constraints, one-page HLD, ER diagram, API docs, README | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Sections 1, 2, 4, 7 |
| At least 8 tests: balanced entries, rounding, settlement formula, reversal, duplicate retry, oversell race, report reconciliation, role access | Section 6 |
| Seed data: at least 5 farmers, 5 buyers, 10 lots, one month of entries | |
| Demo: one lot from arrival to settlement, a correction, a statement, the rokad | Section 8 |

### Constraints
- TypeScript preferred. PostgreSQL preferred.
- No real payment integration. Payments are recorded, not processed.
- Separate presentation, business logic, data access, reporting.
- Runs locally from a clean clone.
- Optional: voice or photo of the paper khata. Not required, and must never auto-post.

### Technical discussion (30–45 min)
Walk through the ledger model and a balanced entry, the settlement formula, how reversal keeps history, retry and concurrency safety, how reports reconcile, and the live correction.
