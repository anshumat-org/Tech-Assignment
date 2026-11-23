# Samples

**v0.1 DRAFT — 2026-11-23** · Look-and-feel references only. They are **not** solutions.

All names, numbers and definitions are placeholders. None of them is a correct answer to the assignment.

| File | Screen or output | Shows |
|---|---|---|
| [S-01-generate-data-command.svg](screens/S-01-generate-data-command.svg) | S-01 · Generate data command (CLI) | Seed, days, output folder and bad-data summary |
| [S-02-run-day-command.svg](screens/S-02-run-day-command.svg) | S-02 · Run day command (CLI, incremental) | Target day, run id, counts, failed exit status |
| [S-03-full-rebuild-command.svg](screens/S-03-full-rebuild-command.svg) | S-03 · Full rebuild command (CLI) | Rebuild all layers; run id, counts, success exit |
| [S-04-dq-test-report.svg](screens/S-04-dq-test-report.svg) | S-04 · DQ test command and report | Tests with type, severity, result, failing rows |
| [S-05-raw-input-files.svg](screens/S-05-raw-input-files.svg) | S-05 · Raw input files | Per-day file list with one missing file |
| [S-06-raw-tables.svg](screens/S-06-raw-tables.svg) | S-06 · raw tables | Rows as in file plus source file and load timestamp |
| [S-07-staging-tables.svg](screens/S-07-staging-tables.svg) | S-07 · staging tables | Typed columns and dedupe outcome |
| [S-08-model-tables.svg](screens/S-08-model-tables.svg) | S-08 · model tables (dim_customer, fact_orders) | Keys and constraints; stale banner |
| [S-09-rejects-table.svg](screens/S-09-rejects-table.svg) | S-09 · rejects table | Bad rows with reason code, source file, run id |
| [S-10-run-log-table.svg](screens/S-10-run-log-table.svg) | S-10 · run log table | Runs with counts and success, failed, running status |
| [S-11-rerun-proof-output.svg](screens/S-11-rerun-proof-output.svg) | S-11 · Rerun proof output | Counts or checksums after run 1 and run 2; match |
| [S-12-forced-failure-demo.svg](screens/S-12-forced-failure-demo.svg) | S-12 · Forced-failure demo output | Model counts before and after; run status failed |
| [S-13-lineage-note.svg](screens/S-13-lineage-note.svg) | S-13 · Lineage note | Path from file to model and per-column transform rows |
| [S-14-readme.svg](screens/S-14-readme.svg) | S-14 · README | Section outline of the README in draft |
| [S-15-new-rule-demo.svg](screens/S-15-new-rule-demo.svg) | S-15 · New-rule demo output | Rule, test result, rows sent to rejects, unrelated tables unchanged |
