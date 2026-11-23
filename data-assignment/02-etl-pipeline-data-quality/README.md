# Assignment 02 — ETL Pipeline & Data Quality

**v0.4 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | A small pipeline that ingests raw files, cleans and models them into tables, with data-quality tests and lineage notes |
| Why | Tests data engineering fundamentals: idempotency, incremental loads, quality gates and handling of bad data |
| Who | A data engineer who owns a pipeline that others rely on |
| How | Any language. SQL required for transforms. PostgreSQL, DuckDB or SQLite. Orchestrators optional, a plain script or Makefile is fine |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Runs locally from a clean checkout, no paid infrastructure |
| Which | Choose it to show data engineering depth |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Language | Any language. SQL required for transforms | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/python/python-original.svg" alt="Python" title="Python (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/postgresql/postgresql-original.svg" alt="SQL" title="SQL" height="32"> |
| Database | PostgreSQL, DuckDB or SQLite | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" title="PostgreSQL" height="32"> <img src="https://cdn.jsdelivr.net/npm/simple-icons@v11/icons/duckdb.svg" alt="DuckDB" title="DuckDB" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/sqlite/sqlite-original.svg" alt="SQLite" title="SQLite" height="32"> |
| Orchestration | Plain script or Makefile is fine. Orchestrator optional | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/bash/bash-original.svg" alt="Shell" title="Shell / Makefile" height="32"> |
| Not required | Streaming, Kubernetes, paid tools, mandatory cloud | — |

## Evaluation weights

| Area | Weight |
|---|---|
| Idempotency and incremental loading | 25% |
| Data-quality tests and failure behaviour | 20% |
| Bad-row handling and auditability | 15% |
| Data model and SQL transforms | 15% |
| Code structure and reuse | 10% |
| Lineage and documentation | 10% |
| Reproducibility (run from raw inputs) | 5% |
| **Total** | **100%** |

Scheduler or tool choice is secondary to correct, repeatable behaviour.

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../README.md](../README.md)
- [../data-instructions.md](../data-instructions.md) (mandatory for every assignment)
