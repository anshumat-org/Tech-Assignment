# Assignment 03 — Observability & Incident Response

**v0.3 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | Metrics, logs, alerts and SLOs for a small sample service, plus a runbook and a blameless write-up of a simulated failure |
| Why | Tests whether the candidate can detect, diagnose and learn from failure, not only build |
| Who | A DevOps or SRE engineer who is on call for the service |
| How | Any stack. Prometheus, Grafana and a log aggregator via Docker Compose are suggested. Equivalents allowed. Failure is injected by the candidate |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Runs locally. No real accounts or paid services |
| Which | Third assignment of the DevOps track, after 01 and 02. Can stand alone |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Sample service | Any stack | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/nodejs/nodejs-original.svg" alt="Node.js" title="Node.js (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/python/python-original.svg" alt="Python" title="Python (example)" height="32"> |
| Metrics and dashboards | Prometheus and Grafana suggested, equivalents allowed | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/prometheus/prometheus-original.svg" alt="Prometheus" title="Prometheus" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/grafana/grafana-original.svg" alt="Grafana" title="Grafana" height="32"> |
| Logs | A log aggregator of your choice | — |
| Runtime | Docker Compose. Local or free tools only | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/docker/docker-original.svg" alt="Docker" title="Docker Compose" height="32"> |

## Evaluation weights

| Area | Weight |
|---|---|
| Metrics, logs and dashboard quality | 20% |
| SLO and alert design | 25% |
| Runbook quality | 15% |
| Incident response and diagnosis | 20% |
| Blameless write-up and follow-up actions | 15% |
| Reproducibility and repo conventions | 5% |
| **Total** | **100%** |

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../README.md](../README.md) (track index)
- [../devops-instructions.md](../devops-instructions.md) (mandatory for every assignment)
