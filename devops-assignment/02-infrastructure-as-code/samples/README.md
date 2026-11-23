# Assignment 02 — Infrastructure as Code — Samples

**v0.1 DRAFT — 2026-11-23** · Look-and-feel references only. They are **not** solutions.

| File | Interface | Shows |
|---|---|---|
| [S-01-plan-command.svg](screens/S-01-plan-command.svg) | S-01 Plan command | Placeholder plan output, summary counts, destroy flag |
| [S-02-apply-command.svg](screens/S-02-apply-command.svg) | S-02 Apply command | Confirmation prompt, per-resource output, lock error |
| [S-03-clean-rebuild.svg](screens/S-03-clean-rebuild.svg) | S-03 Clean rebuild sequence | Ordered init → plan → apply from clean checkout |
| [S-04-plan-review-pr.svg](screens/S-04-plan-review-pr.svg) | S-04 Plan review on PR | Generic code-host PR with per-env plan summaries |
| [S-05-production-approval-gate.svg](screens/S-05-production-approval-gate.svg) | S-05 Production approval gate | Plan summary, destroy warning, approve/reject |
| [S-06-destroy-safeguard.svg](screens/S-06-destroy-safeguard.svg) | S-06 Destroy safeguard | Plan blocked by protected resource, override note |
| [S-07-state-backend-lock.svg](screens/S-07-state-backend-lock.svg) | S-07 State backend and lock | Backend location, lock holder, unlock steps |
| [S-08-secrets-manager.svg](screens/S-08-secrets-manager.svg) | S-08 Secrets manager | Secret names, versions, rotate/revoke; values hidden |
| [S-09-temporary-access.svg](screens/S-09-temporary-access.svg) | S-09 Temporary access grant and revoke | Request → grant → expiry → revoke with details |
| [S-10-env-variable-files.svg](screens/S-10-env-variable-files.svg) | S-10 Per-environment variable files | Diff with lines as bars (no real code), per-env changes |
| [S-11-drift-check.svg](screens/S-11-drift-check.svg) | S-11 Drift check | Diff list of out-of-band changes, drift flag |
| [S-12-service-reachability.svg](screens/S-12-service-reachability.svg) | S-12 Sample service reachability check | JSON response from service, reachable/unreachable |
| [S-13-access-matrix.svg](screens/S-13-access-matrix.svg) | S-13 Access matrix | Identity × purpose × permissions table, placeholders |
| [S-14-readme-design-cost-note.svg](screens/S-14-readme-design-cost-note.svg) | S-14 README, design note and cost note | Document preview with section headings |

All values are placeholders. No real pipeline, infrastructure or alerting configuration is shown; design your own.
