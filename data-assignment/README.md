# Data Assignments

**v0.5 DRAFT — 2026-11-23**

| # | Assignment | Best for | Focus | Effort | Review | Folder |
|---|---|---|---|---|---|---|
| 01 | SQL Analytics & Metrics | Analysts, analytics engineers | Metric definitions, denominators, window functions, CTEs, cohort retention | 4–6 h | 20–30 min | [01-sql-analytics-metrics](01-sql-analytics-metrics/README.md) |
| 02 | ETL Pipeline & Data Quality | Data engineers | Idempotent loads, incremental runs, DQ tests, bad rows, lineage | 6–8 h | 30–45 min | [02-etl-pipeline-data-quality](02-etl-pipeline-data-quality/README.md) |
| 03 | KPI Dashboard & Insight Report | Analysts, BI developers | KPI definitions, caveats, reconciliation, honest charts | 6–8 h | 30–45 min | [03-kpi-dashboard-insight-report](03-kpi-dashboard-insight-report/README.md) |

**Choose any one assignment below and complete only that one.** Not sure? 01 covers SQL and metrics, 02 suits data engineering, 03 suits analysis and reporting.

## Tech stack

SQL is required in every assignment. The rest is your choice.

| # | Language / framework | Database / storage | Tools, mocks and hosting | Flexibility |
|---|---|---|---|---|
| 01 | SQL for all analysis; any language for data generation | PostgreSQL, DuckDB or SQLite | No BI tool needed | Any language for the data generator |
| 02 | Any language; SQL for transforms | PostgreSQL, DuckDB or SQLite | Plain script or Makefile is fine; orchestrator optional | No streaming, Kubernetes, paid tools or mandatory cloud |
| 03 | SQL for metrics; any BI tool or code (Streamlit, Metabase, Superset, notebook, static HTML) | PostgreSQL, DuckDB or SQLite | No paid tool or cloud service required | Any BI tool |

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
| `product-brief.md` | Start here. What you build: product, personas, journey, capabilities, user stories with acceptance criteria |
| `requirements-and-directives.md` | Part 1 requirements and scenarios. Part 2 do / don't rules, deliverables, constraints, discussion |
| `resources.md` | Reference links for the topic. Starting points, not solutions |
| `developer-guide.md` | Build order, directions, and before / during / after checklists |

## Data

No dataset is shipped. Generate synthetic data yourself, or work from the schema described in your assignment.
