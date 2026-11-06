# Assignment 03 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Instrumentation

| Signal | Minimum expectation |
|---|---|
| Metrics | Request rate, error rate, latency percentiles, saturation of one resource |
| Logs | Structured, with request ID and severity. No personal or secret data |
| Dashboard | One view an on-call engineer can read in 30 seconds |

### B. SLOs
- Define at least two SLIs (for example availability and latency) with targets and a window.
- Show the error budget and how it is calculated.
- State what happens when the budget is nearly spent.

### C. Alerts
- Alert on symptoms users feel, not on every cause.
- Each alert has severity, an owner, a runbook link and a stated reason.
- Use burn-rate or multi-window logic for at least one alert, or justify a simpler rule.
- Document how you avoid noisy and flapping alerts.

### D. Runbook
- A runbook for the main alert: impact, first checks, likely causes, mitigation, rollback, escalation.
- Written so someone new can follow it at 3 a.m.

### E. Simulated incident
- Inject one realistic failure (for example a slow dependency, a bad deploy, a memory leak or an exhausted connection pool).
- Show detection by an alert, diagnosis using your telemetry, and mitigation.
- Write a blameless incident report: timeline, impact, root cause, detection gap, what went well and badly, action items with owners.

### F. Engineering scenarios (answer in README)
- The alert never fired. What do you change?
- Alerts fire at night but users report nothing. What do you review?
- How would you cap log and metric cost as traffic grows?
- Which telemetry would you add before the next release?
- How do you decide between rollback and fix-forward?

### G. Live follow-up
The interviewer may inject a new failure or ask you to add an alert and an SLO for a new endpoint. Show the signal, the alert firing and the runbook step. Structure configuration so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Alert on user-visible symptoms with a runbook link | Alert on every metric or without an owner |
| Define SLOs with a window and an error budget | Pick targets with no reasoning |
| Use structured logs with request IDs | Log secrets or personal data |
| Write the incident report in blameless language | Name or blame individuals |
| Give each action item an owner and a due date | List vague follow-ups |
| Keep dashboards focused and readable | Fill dashboards with unused panels |
| Keep configuration in the repo | Build dashboards by hand without exporting them |

### Deliverables

| Item | Detail |
|---|---|
| Git repo with sample service, telemetry config, README | Setup instructions and meaningful commits |
| Dashboard and alert rules | Exported as code |
| SLO document | SLIs, targets, window, error budget |
| Runbook | For the primary alert |
| Incident report | Timeline, root cause, actions. See [../devops-instructions.md](../devops-instructions.md) |
| Evidence | Screenshots or logs of detection, diagnosis, recovery |
| Scenario answers | Section F in the README |

### Constraints
- Local or free tools only. Any stack.
- Synthetic traffic and data only. No real accounts or keys.
- The incident is simulated. Say clearly how you triggered it.
- AI assistance allowed. You verify and own the analysis.

### Technical discussion (30–45 min)
Walk through the SLO choice, one alert and its runbook, and the incident timeline. Explain the detection gap and the top action item. Expect a live injected failure or a new alert request. Show the change reviewed before it is applied.
