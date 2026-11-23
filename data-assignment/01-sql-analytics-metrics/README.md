# Assignment 01 — SQL Analytics & Metrics

**v0.4 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | Answer business questions on a synthetic retail sales dataset using SQL: metric definitions, window functions, CTEs and a cohort retention query |
| Why | Tests SQL depth, precise metric definitions, denominators and awareness of messy data |
| Who | An analyst who turns a business question into a defined, verifiable number |
| How | SQL required. PostgreSQL, DuckDB or SQLite. Any language for data generation. Candidate generates data or builds from the given schema |
| When | 4–6 hours of effort. Review 20–30 minutes |
| Where | Runs locally, no paid infrastructure |
| Which | Choose it to show SQL and metric-definition depth |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Analysis | SQL (required) | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/postgresql/postgresql-original.svg" alt="SQL" title="SQL" height="32"> |
| Database | PostgreSQL, DuckDB or SQLite | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" title="PostgreSQL" height="32"> <img src="https://cdn.jsdelivr.net/npm/simple-icons@v11/icons/duckdb.svg" alt="DuckDB" title="DuckDB" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/sqlite/sqlite-original.svg" alt="SQLite" title="SQLite" height="32"> |
| Data generation | Any language | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/python/python-original.svg" alt="Python" title="Python (example)" height="32"> |
| Tools | No BI tool needed. Runs locally | — |

## Evaluation weights

| Area | Weight |
|---|---|
| Metric definitions and denominators | 25% |
| SQL correctness and readability (CTEs, windows) | 25% |
| Cohort / retention logic | 15% |
| Data-quality awareness and edge cases | 15% |
| Reconciliation and verification | 10% |
| Documentation of assumptions and limits | 10% |
| **Total** | **100%** |

Clever SQL is secondary to correct, explained numbers.

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../README.md](../README.md)
- [../data-instructions.md](../data-instructions.md) (mandatory for every assignment)
