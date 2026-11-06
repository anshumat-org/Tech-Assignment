# Data Assignments

**v0.1 DRAFT — 2026-11-06**

> DRAFT: content is not final and may change before it is sent to candidates.

| # | Assignment | Best for | Focus | Effort | Review | Folder |
|---|---|---|---|---|---|---|
| 01 | SQL Analytics & Metrics | Analysts, analytics engineers | Metric definitions, denominators, window functions, CTEs, cohort retention | 4–6 h | 20–30 min | [01-sql-analytics-metrics](01-sql-analytics-metrics/README.md) |
| 02 | ETL Pipeline & Data Quality | Data engineers | Idempotent loads, incremental runs, DQ tests, bad rows, lineage | 6–8 h | 30–45 min | [02-etl-pipeline-data-quality](02-etl-pipeline-data-quality/README.md) |
| 03 | KPI Dashboard & Insight Report | Analysts, BI developers | KPI definitions, caveats, reconciliation, honest charts | 6–8 h | 30–45 min | [03-kpi-dashboard-insight-report](03-kpi-dashboard-insight-report/README.md) |

**Recommended order:** start with 01 for every Data candidate. Then choose 02 (engineering focus) or 03 (analysis and communication focus). Do not ask every applicant to complete all three.

## Rules for candidates

- Complete only the assignment selected for you.
- Read [data-instructions.md](data-instructions.md) first. It applies to every assignment.
- Synthetic data only. No personal data, no real company data.
- Humans own definitions, approval and conclusions. AI assistance must be disclosed and verified.
- Make results reproducible from raw inputs, with setup instructions in your README.
- Submission window 3 calendar days, then a technical discussion.
- Use PostgreSQL, DuckDB or SQLite. SQL is required in every assignment.

## Each assignment folder contains

| File | Purpose |
|---|---|
| `README.md` | Overview (WH table), evaluation weights, read-next links |
| `requirements-and-directives.md` | Part 1 requirements and scenarios. Part 2 do / don't rules, deliverables, constraints, discussion |
| `resources.md` | Reference links for the topic. Starting points, not solutions |

## Status

| Item | State |
|---|---|
| Content | DRAFT v0.1, under review |
| Sample data | Candidate generates it, or receives only the schema. No dataset is shipped yet |
