# Assignment 02 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Raw inputs (synthetic)

| File | Suggested content |
|---|---|
| `customers_YYYYMMDD.csv` | customer_id, signup_date, region, updated_at |
| `orders_YYYYMMDD.csv` | order_id, customer_id, order_ts, status, amount, currency |
| `events_YYYYMMDD.jsonl` | event_id, customer_id, event_type, event_ts |

- Generate daily files for 10–14 days with a seeded script. Ids are opaque synthetic keys, no personal data.
- Seed bad data: duplicate keys, NULLs in required fields, malformed dates, negative amounts, unknown currency, orphan customer ids.

### B. Layers

| Layer | Purpose |
|---|---|
| raw | Files loaded as-is with source file name and load timestamp |
| staging | Typed, cleaned, deduplicated |
| model | Dimension and fact tables (for example dim_customer, fact_orders) |
| rejects | Rows that failed rules, with reason code and source file |

### C. Pipeline behaviour
- **Idempotent:** running the same file or day twice gives the same final tables.
- **Incremental:** a new day processes only new or changed data. Full rebuild must also work.
- **Atomic:** a failed run leaves the model tables unchanged.
- Run log table: run id, start, end, rows read, loaded, rejected, status.

### D. Data-quality tests

| Type | Example |
|---|---|
| Uniqueness | order_id unique in fact_orders |
| Not null | customer_id, order_ts required |
| Referential | every order maps to a customer, or goes to rejects |
| Range / domain | amount >= 0, status in allowed list |
| Volume / freshness | row count within expected band, latest file date |

State which tests block the run and which only warn, and why.

### E. Scenarios to address (README)
- **Late-arriving data:** a file for day 3 arrives after day 5 was processed.
- **Duplicates:** the same order appears in two files with different values. Which wins?
- **Nulls:** a required field is NULL. Reject, default or quarantine?
- **Definition change:** status values are renamed upstream, or currency becomes mandatory.
- **Schema drift:** an unexpected extra column appears.

### F. Lineage notes
One table or diagram: source file to raw, staging, model, and which transform touches which column.

### G. Live follow-up
The interviewer may add a new rule (for example, reject orders older than 90 days) or a new source column. Add it with a test and show that unrelated tables and rows are unchanged.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Use keys and upserts or merge so reruns are safe | Append blindly and rely on running once |
| Keep raw data untouched and replayable | Edit raw files by hand |
| Send bad rows to a rejects table with a reason | Drop bad rows silently or crash on the first one |
| Wrap model updates in a transaction | Leave half-loaded tables after a failure |
| Keep rules and transforms in one place and reuse them | Duplicate cleaning logic per source |
| Log counts per run and explain material changes | Report success without row counts |
| Disclose AI-generated code and verify it | Submit code you cannot explain |

### Deliverables

| Item | Format |
|---|---|
| Git repo with setup instructions, meaningful commits | Runs from a clean checkout in one or two commands |
| Seeded data generator and sample raw files | Synthetic only |
| Pipeline code and SQL transforms | Layers as in section B |
| Schema or DDL for all layers, including rejects and run log | Keys and constraints noted |
| Data-quality tests with passing and failing demonstration | Automated |
| Lineage note | Table or Mermaid diagram |
| README with assumptions, trade-offs and answers to scenarios in E | Short bullets |
| Rerun proof | Output showing identical results after a second run |

### Constraints
- Any language. SQL required for transforms.
- PostgreSQL, DuckDB or SQLite acceptable.
- No mandatory cloud service or paid tool. An orchestrator is optional.
- Synthetic data only. No personal data.
- Keep scope small: no streaming, no Kubernetes.

### Technical discussion (30–45 min)
Walk through the layers, show a rerun and a late file, explain one rejected row end to end, say which test would catch the most likely failure, and describe what you would monitor. Expect a live rule change.
