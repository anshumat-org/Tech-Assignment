# Assignment 06 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 8–10 hours on ledger correctness, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Schema: accounts, parties, lots, journal entries and lines, idempotency keys, audit | Migrations run from clean. DB rejects an unbalanced entry or an update of a posted entry | 1.5 h |
| 2 | Posting service: one function that writes a balanced entry in a transaction | Unit tests for balance, rounding and idempotency pass | 1.5 h |
| 3 | Lots and sales (with oversell protection) | Two parallel sales cannot exceed lot quantity | 1 h |
| 4 | Advances, receipts, payments | Party balance changes by exactly the posted lines | 1 h |
| 5 | Settlement preview and post | Preview figures equal posted figures | 1.5 h |
| 6 | Reversal and re-post | Statement shows original, reversal and new entry. All balanced | 1 h |
| 7 | Reports: statement, rokad, outstanding, lot summary | Each report reconciles to ledger lines | 1 h |
| 8 | UI, Hindi / English toggle, entry preview | A munshi can post a sale in under 30 seconds | 1 h |
| 9 | Tests, seed data, docs, demo | Checklist C is complete | 1 h |

Build the ledger and posting service first. UI polish comes last.

## 2. Directions

| Topic | Direction |
|---|---|
| Money | Integer paise. Convert only at the edges (input and display) |
| Quantity | Decimal with a stated precision (for example 3 places). Never float |
| One write path | Every money movement goes through the posting service. No route writes ledger lines directly |
| Immutability | Add a DB trigger or revoke UPDATE/DELETE on journal tables. Say which you used |
| Balances | Compute from lines. If you cache, show how it is verified against the ledger |
| Corrections | Reverse the original, then post the new entry. Link them and store the reason |
| Idempotency | Require an `Idempotency-Key` header on all POSTs that post entries. Same key and same body returns the same result. Same key with a different body is an error |
| Concurrency | Lock the lot row (`SELECT … FOR UPDATE`) or use a constraint, and test it |
| Roles | Owner: everything. Munshi: post entries, cannot reverse a settlement. Viewer: read only. Enforce server-side |
| Language | Keep labels in translation files. Reports and prints use the active language |
| AI or OCR | Not required. If you add it, it must never post without a human preview |
| Scope | If you skip something, list it under "Limitations" in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../developer-instructions.md](../developer-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 06 (not another one)
- [ ] Write down your assumptions about mandi rules (commission base, rounding, closed periods, day boundary)
- [ ] Choose stack: TypeScript and PostgreSQL preferred. Note any change and why
- [ ] Verify Node (or runtime), PostgreSQL and package manager work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Sketch the chart of accounts and one example entry for each of: sale, advance, receipt, settlement
- [ ] Draft the ER diagram and a one-page HLD (Mermaid is fine)
- [ ] Plan the 9 steps above against your available hours
- [ ] Decide the 8 tests you will write (see requirements)
- [ ] Prepare synthetic seed data plan: 5 farmers, 5 buyers, 10 lots, one month of entries

## 4. Checklist B — While developing

### Ledger and money
- [ ] No floating point for money anywhere (search the code for `parseFloat`, `Number(` on money)
- [ ] Every entry balances. Test with a deliberately unbalanced entry and confirm it is rejected
- [ ] Rounding rule is implemented once, in one function, and tested with ₹1,234.56 at 2.5%
- [ ] Posted lines cannot be updated or deleted (try it in a test)
- [ ] Reversal mirrors the original lines, links to it, and stores reason and actor

### Business logic
- [ ] Sale cannot exceed remaining lot quantity, even with two parallel requests
- [ ] Deductions show rate and base on each line
- [ ] Advances larger than proceeds produce a negative net payable that is shown and carried forward
- [ ] Preview and post of a settlement use the same code and return the same figures
- [ ] Deduction rate lookup uses effective-from date
- [ ] Receipt allocation across several open sales works, and a manual override is possible
- [ ] Closed-period behaviour is implemented as you documented

### API and security
- [ ] All routes validate input with a schema and return consistent errors
- [ ] Idempotency keys implemented on all posting endpoints
- [ ] Business ID and role come from the session, not from the request body
- [ ] Audit event written for every post, reversal and settlement
- [ ] No secrets, tokens or real personal data in code, logs or seed data

### UI
- [ ] Hindi / English toggle changes every label, error and report
- [ ] Entry preview shows Dr/Cr lines and balance before and after, with Post and Cancel
- [ ] Reversed entries marked with text and icon, not colour alone
- [ ] Works at phone width. Devanagari renders correctly

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go (you must disclose it)

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Migrate, seed, start, test. All work
- [ ] All tests pass. At least 8 cover: balanced entries, rounding, settlement formula, reversal, duplicate retry, oversell race, report reconciliation, role access
- [ ] Reconciliation check: sum of statements, rokad and outstanding all agree with ledger lines
- [ ] Live-change rehearsal: reverse a settlement after a rate correction and re-post it. Statements, outstanding and rokad still balance

### Deliverables
- [ ] HLD (one page) and ER diagram, per SUBMISSION_FORMATS.md
- [ ] Schema or migrations with constraints and indexes
- [ ] API docs for every endpoint
- [ ] Seed data loads: 5 farmers, 5 buyers, 10 lots, one month of entries
- [ ] Demo (video or screenshots): lot from arrival to settlement, a correction, a statement, the rokad
- [ ] README contains: setup, run, test, assumptions, rounding and day-boundary rules, closed-period rule, trade-offs, limitations, future work, AI usage disclosure, sources cited

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can explain a balanced entry end to end
- [ ] Can explain the settlement formula and the preview vs post guarantee
- [ ] Can explain how reversal keeps history and how reports stay consistent
- [ ] Can explain retry and concurrency safety
- [ ] Ready to do the live change: reverse and re-post a settlement

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Storing balance in a column and updating it | Derive from lines, or verify the cache |
| Editing a wrong entry in place | Reverse and re-post |
| Float arithmetic on rupees | Integer paise |
| Rounding in several places | One rounding function |
| Idempotency only in the UI | Enforce on the server |
| Role from a request header you trust | Role from the authenticated session |
| Report totals typed or cached separately | Compute from ledger lines |
| Perfect UI, thin ledger tests | Ledger and settlement first |
