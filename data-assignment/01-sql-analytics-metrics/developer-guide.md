# Assignment 01 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 4–6 hours on correct, explained numbers, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Schema and seeded data generator (10k+ orders, 18–24 months, fixed seed, deliberate mess) | Clean checkout builds the database. Same seed gives the same rows | 1 h |
| 2 | `metrics.md`: definition, denominator, grain, limits for the 5 metrics | Written before any query. Every metric has a stated base | 0.75 h |
| 3 | Shared views or CTEs (for example net revenue, valid orders) | One place holds status, discount, return and NULL handling | 0.75 h |
| 4 | Queries 1–3: monthly revenue with LAG, top 3 per category, 3-month rolling average | Each runs from its own SQL file and result is saved | 1 h |
| 5 | Queries 4–5: cohort retention (months 0–6), top 10% revenue share | Cohort sizes sum to customers. Retention at month 0 is explained | 1 h |
| 6 | Verification: one two-way reconciliation and at least 3 sanity checks | Script or query prints pass / fail | 0.25 h |
| 7 | README: assumptions, scenarios D, AI usage. Rehearse the live definition change | Checklist C is complete | 0.25 h |

Total 5 h (range 4–6 h). Write definitions first. Clever SQL comes last.

## 2. Directions

| Topic | Direction |
|---|---|
| Definitions first | Write each metric's definition, denominator, grain and limits in `metrics.md` before the query |
| Engine | PostgreSQL, DuckDB or SQLite. SQL for all analysis. Any language for data generation |
| Data | Synthetic only. Opaque customer ids. No names, emails or phones. Fixed random seed |
| Seeded mess | Include duplicate rows, NULL discounts, cancelled orders, orders with no items |
| Shared logic | Put net revenue and similar rules in one view or CTE. Do not copy filters into each query |
| Structure | CTEs with clear names and one purpose each. One SQL file per question |
| Handling rules | State how NULLs, duplicates and cancelled rows are treated. Never drop rows silently |
| Verification | Reconcile one total two ways. List at least 3 sanity checks |
| Live change | Make "any order" vs "paid order only" (or excluding a channel) a change in one place |
| AI | Allowed if disclosed. You must explain and verify every query |
| Scope | No BI tool needed. If you skip something, say so in the README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../data-instructions.md](../data-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 01 (not another one)
- [ ] Choose the engine (PostgreSQL, DuckDB or SQLite) and check it runs locally
- [ ] Create a new git repo with a README skeleton and `.gitignore`
- [ ] Decide the data generator language and the random seed
- [ ] List your open assumptions: which order statuses count as revenue, how returns are netted, what the repeat-rate base is
- [ ] Plan the 7 steps above against your available hours
- [ ] Decide the sanity checks you will run (row counts, no negative revenue, cohort sizes sum to customers)

## 4. Checklist B — While developing

### Data and definitions
- [ ] Generator is seeded and produces 10k+ orders over 18–24 months
- [ ] Mess is seeded: duplicates, NULL discounts, cancelled orders, orders with no items
- [ ] Each of the 5 metrics has definition, denominator, grain and known limits
- [ ] Net revenue states statuses counted and treatment of discounts and returns
- [ ] Return rate states units or value, and the period

### SQL
- [ ] Q1 monthly net revenue with month-over-month change (CTE + LAG)
- [ ] Q2 top 3 products per category (RANK / ROW_NUMBER). Tie handling stated
- [ ] Q3 3-month rolling average with an explicit window frame
- [ ] Q4 cohorts by signup month with retention at months 0 to 6
- [ ] Q5 share of revenue from the top 10% of customers (NTILE or running total)
- [ ] Shared logic lives in one view or CTE. No filter copied across queries
- [ ] Non-obvious logic is commented

### Quality and verification
- [ ] Duplicates are detected and removed without losing real rows. Counts shown
- [ ] NULL discount and NULL cost handling is chosen, stated and justified
- [ ] No negative revenue, no double counting after joins
- [ ] Reconciliation runs: sum of monthly revenue equals the total from order_items
- [ ] Cohort sizes sum to the number of customers

### Habits
- [ ] Check results against a known figure before trusting them
- [ ] Commit small and often with meaningful messages
- [ ] Record any AI tool usage as you go (you must disclose it)
- [ ] No personal data or secrets anywhere

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Generate data, build views, run every query. All work
- [ ] Verification script runs and shows the reconciliation and the sanity checks
- [ ] Live-change rehearsal: switch retention from "any order" to "paid order only" (or exclude one channel) in one place. Say which numbers move

### Deliverables
- [ ] Git repo with setup steps and a seeded data generator or schema script
- [ ] `metrics.md` with definitions, denominators and limits in one table
- [ ] SQL files, one per question, plus shared views
- [ ] Result tables or screenshots for each query, reproducible from raw inputs
- [ ] Verification output (reconciliation and sanity checks)
- [ ] README with assumptions and short-bullet answers to the 4 scenarios: late-arriving data, duplicates, nulls, definition change (returns by return date)
- [ ] AI usage disclosure and sources cited, per [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead queries, stray debug output or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (20–30 min)
- [ ] Can walk through one metric definition and its denominator
- [ ] Can explain the cohort query step by step
- [ ] Can show a reconciliation and say what you would verify next
- [ ] Can identify and explain any AI-generated SQL
- [ ] Ready for the live definition change

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Defining a metric by whatever the query returns | Write definition and denominator first |
| Same filter copied into every query | One shared view or CTE |
| Join fan-out inflating revenue | Check row counts before and after each join |
| Silently dropping NULLs or duplicates | State the rule, show the counts |
| Cohort month 0 unexplained or cohort sizes not summing to customers | Explain month 0 and add the sum check |
| Trusting a plausible number | Reconcile two ways and show the check |
| Deeply nested subqueries | Named CTEs, one purpose each |
| Overclaiming what the data proves | Document the limits of each metric |
