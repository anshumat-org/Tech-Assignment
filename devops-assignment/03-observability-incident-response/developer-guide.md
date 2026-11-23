# Assignment 03 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on SLOs, alerts and a real incident write-up, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Sample service with metrics and structured logs (request ID, severity) | Request rate, error rate, latency percentiles and one saturation metric are exposed | 1 h |
| 2 | Telemetry stack (for example Prometheus, Grafana, log aggregator via Docker Compose) | One command starts it. Metrics and logs are visible | 1 h |
| 3 | Dashboard | An on-call engineer can read it in 30 seconds. Exported as code | 0.75 h |
| 4 | SLIs, SLOs and error budget | At least two SLIs with targets and window. Budget calculation and low-budget policy written | 1 h |
| 5 | Alert rules | Symptom-based alerts with severity, owner, runbook link and reason. Burn-rate or multi-window for at least one | 1 h |
| 6 | Runbook for the main alert | Covers impact, first checks, likely causes, mitigation, rollback, escalation | 0.75 h |
| 7 | Simulated incident | Failure injected. Detection by alert, diagnosis from telemetry and mitigation are evidenced | 1 h |
| 8 | Incident report, scenario answers, README | Checklist C is complete | 1.5 h |

Get telemetry flowing before writing alerts. Write the report while the incident is fresh.

## 2. Directions

| Topic | Direction |
|---|---|
| Signals | Metrics for rate, errors, latency percentiles and one saturation. Logs are structured with request ID and severity |
| Log content | No personal or secret data in logs |
| Dashboard | Focused and readable. No unused panels |
| SLOs | At least two SLIs with targets, a window and a reasoned target. Show the error budget and what happens when it is nearly spent |
| Alerts | Alert on symptoms users feel. Each has severity, owner, runbook link and reason |
| Alert quality | Use burn-rate or multi-window logic for at least one alert, or justify a simpler rule. Say how you avoid noise and flapping |
| Runbook | Written so someone new can follow it at 3 a.m. |
| Incident | Inject one realistic failure. Say clearly how you triggered it |
| Report | Blameless language. No naming or blaming individuals. Action items have an owner and a due date |
| Config as code | Dashboards and alert rules live in the repo. Do not build by hand without exporting |
| Data | Synthetic traffic and data only. Local or free tools only |
| AI use | Allowed. You verify and own the analysis. Record usage ([../devops-instructions.md](../devops-instructions.md)) |
| Scope gaps | If you skip something, list it under known limits in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../devops-instructions.md](../devops-instructions.md) and [../README.md](../README.md)
- [ ] Confirm you are doing Assignment 03 (not another one)
- [ ] Choose service language and telemetry stack. Note any change from the suggested one and why
- [ ] Verify Docker and Docker Compose work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] No real accounts or paid services. Synthetic traffic only
- [ ] Choose the failure you will inject and how you will trigger it
- [ ] Draft candidate SLIs and targets with your reasoning
- [ ] Write down assumptions
- [ ] Plan the 8 steps above against your available hours
- [ ] Read the five scenarios in section F so your design can answer them

## 4. Checklist B — While developing

### Instrumentation
- [ ] Request rate, error rate, latency percentiles and one saturation metric are present
- [ ] Logs are structured and carry request ID and severity
- [ ] No personal or secret data in logs
- [ ] Dashboard is readable in 30 seconds and exported as code

### SLOs
- [ ] At least two SLIs with targets and a window
- [ ] Error budget calculation is shown
- [ ] Policy for a nearly spent budget is stated

### Alerts and runbook
- [ ] Alerts target user-visible symptoms
- [ ] Each alert has severity, owner, runbook link and reason
- [ ] At least one alert uses burn-rate or multi-window logic, or the simpler rule is justified
- [ ] Noise and flapping controls are documented
- [ ] Runbook covers impact, first checks, likely causes, mitigation, rollback, escalation

### Incident
- [ ] Failure is injected and the trigger method is documented
- [ ] Alert fires. Screenshot or log captured
- [ ] Diagnosis uses your own telemetry. Evidence captured
- [ ] Mitigation and recovery are captured
- [ ] Timeline notes are kept as you go

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Review config changes before applying them
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Start the stack, generate traffic, see the dashboard. All work
- [ ] Alert rules and dashboards load from the repo, not from hand edits
- [ ] Incident replay works: inject, detect, diagnose, mitigate
- [ ] Live-change rehearsal: add an alert and an SLO for a new endpoint and show the signal, the alert firing and the runbook step

### Deliverables
- [ ] Git repo with sample service, telemetry config and README, with setup instructions
- [ ] Dashboard and alert rules exported as code
- [ ] SLO document: SLIs, targets, window, error budget
- [ ] Runbook for the primary alert
- [ ] Incident report: timeline, impact, root cause, detection gap, what went well and badly, action items with owners
- [ ] Evidence: screenshots or logs of detection, diagnosis, recovery
- [ ] README contains: assumptions, how the incident was triggered, answers to scenarios in section F, known limits, AI usage disclosure

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No unused panels, dead alert rules or TODOs that hide gaps
- [ ] Report uses blameless language throughout
- [ ] Commit history is meaningful
- [ ] Submit within 3 calendar days via the route given in the root README

### Prepare for the discussion (30–45 min)
- [ ] Can explain the SLO choice and the error budget
- [ ] Can walk through one alert and its runbook
- [ ] Can walk through the incident timeline
- [ ] Can explain the detection gap and the top action item
- [ ] Ready for a live injected failure or a new alert request, with the change reviewed before applying

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Alerting on every metric or cause | Alert on user-visible symptoms |
| Alerts with no owner or runbook | Add severity, owner, runbook link and reason |
| SLO targets with no reasoning | State why, with a window and error budget |
| Logging request bodies, secrets or personal data | Log request ID and severity only. Review samples |
| Dashboards built by hand and lost | Export as code and commit |
| Blaming a person in the report | Describe causes in systems and process terms |
| Vague follow-ups | Each action has an owner and a due date |
| Dashboard full of unused panels | Keep the 30-second view |
