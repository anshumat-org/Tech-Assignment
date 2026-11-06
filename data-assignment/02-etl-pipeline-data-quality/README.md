# Assignment 02 — ETL Pipeline & Data Quality

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | A small pipeline that ingests raw files, cleans and models them into tables, with data-quality tests and lineage notes |
| Why | Tests data engineering fundamentals: idempotency, incremental loads, quality gates and handling of bad data |
| Who | A data engineer who owns a pipeline that others rely on |
| How | Any language. SQL required for transforms. PostgreSQL, DuckDB or SQLite. Orchestrators optional, a plain script or Makefile is fine |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Runs locally from a clean checkout, no paid infrastructure |
| Which | Stage 2 of the Data funnel, after 01. Pairs with 03 for candidates who also report |

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

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../README.md](../README.md)
- [../data-instructions.md](../data-instructions.md) (mandatory for every assignment)
