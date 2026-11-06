# Assignment 01 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Dataset (synthetic)

| Table | Suggested fields |
|---|---|
| customers | customer_id, signup_date, region, channel |
| products | product_id, category, unit_cost, list_price |
| orders | order_id, customer_id, order_date, status (placed / shipped / cancelled / returned) |
| order_items | order_id, product_id, quantity, unit_price, discount |
| returns | order_id, product_id, return_date, quantity |

- Generate roughly 10k+ orders over 18–24 months with a script and a fixed random seed, or follow the schema above.
- Customer ids are opaque synthetic keys. No names, emails or phones.
- Seed deliberate mess: duplicate rows, NULL discounts, cancelled orders, orders with no items.

### B. Metric definitions (written before SQL)

| Metric | Must state |
|---|---|
| Net revenue | Which statuses count, treatment of discounts and returns |
| Average order value | Numerator, denominator, cancelled orders in or out |
| Repeat purchase rate | Customers with 2+ orders divided by which customer base |
| Return rate | By units or by value, and over which period |
| Gross margin % | Cost source, rows excluded |

Each metric needs: definition, denominator, grain, known limits.

### C. Queries required

| # | Question | Technique |
|---|---|---|
| 1 | Monthly net revenue and month-over-month change | CTE + LAG |
| 2 | Top 3 products per category by revenue | RANK / ROW_NUMBER |
| 3 | 3-month rolling average revenue | Window frame |
| 4 | Customer cohorts by signup month with retention at month 0 to 6 | Cohort + date arithmetic |
| 5 | Share of revenue from top 10% of customers | NTILE or running total |

### D. Scenarios to address (README)
- **Late-arriving data:** orders appear after a month is reported. Which numbers change?
- **Duplicates:** how do you detect and remove them without losing real rows?
- **Nulls:** discount or cost is NULL. Treat as zero, exclude or flag? Why?
- **Definition change:** the business now wants returns netted by return date, not order date. What shifts?

### E. Verification
- Reconcile one total two ways (for example, sum of monthly revenue equals total from order_items).
- List at least three sanity checks (row counts, no negative revenue, cohort sizes sum to customers).

### F. Live follow-up
The interviewer may ask you to change the retention definition from "any order" to "paid order only" or to exclude one channel. Change one definition in one place and show which numbers move.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Write each metric definition and denominator before the query | Define a metric only by what the query happens to return |
| Use CTEs with clear names and one purpose each | Nest deep subqueries nobody can read |
| Put shared logic (for example net revenue) in one view or CTE | Copy the same filter into every query |
| State how NULLs, duplicates and cancelled rows are handled | Silently drop rows |
| Reconcile totals and show the check | Trust a number because it looks plausible |
| Disclose any AI-generated SQL and explain it | Submit queries you cannot explain |
| Document limits of each metric | Overclaim what the data proves |

### Deliverables

| Item | Format |
|---|---|
| Git repo with setup steps and a seeded data generator or schema script | Runs from a clean checkout |
| `metrics.md` with definitions, denominators and limits | One table |
| SQL files, one per question, plus shared views | Commented where logic is non-obvious |
| Result tables or screenshots for each query | Reproducible from raw inputs |
| Verification output (reconciliation and sanity checks) | Script or query |
| README with assumptions and answers to scenarios in D | Short bullets |

### Constraints
- Any language for data generation. SQL is required for all analysis.
- PostgreSQL, DuckDB or SQLite acceptable.
- Synthetic data only. No personal data.
- No BI tool needed for this assignment.

### Technical discussion (20–30 min)
Walk through one metric definition and its denominator, explain the cohort query step by step, show a reconciliation, and say what you would verify next. Expect a live definition change.
