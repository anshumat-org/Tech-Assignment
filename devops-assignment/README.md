# DevOps Assignments

**v0.4 DRAFT — 2026-11-23**

| # | Assignment | Focus | Effort | Review | Folder |
|---|---|---|---|---|---|
| 01 | CI/CD Pipeline | Build, test, security scan, staging deploy, promotion, rollback | 4–6 hours | 30 min | [01-ci-cd-pipeline](01-ci-cd-pipeline/README.md) |
| 02 | Infrastructure as Code | Staging and production environments, secrets, least privilege, rebuild from clean | 6–8 hours | 30–45 min | [02-infrastructure-as-code](02-infrastructure-as-code/README.md) |
| 03 | Observability & Incident Response | Metrics, logs, alerts, SLOs, runbook, blameless incident write-up | 6–8 hours | 30–45 min | [03-observability-incident-response](03-observability-incident-response/README.md) |

**Choose any one assignment below and complete only that one.** Not sure? 01 covers CI/CD, 02 suits infrastructure as code, 03 suits observability and incident response.

## Rules for candidates

| Rule | Detail |
|---|---|
| Scope | Complete only the assignment selected for you |
| Principles | Read [devops-instructions.md](devops-instructions.md). It applies to every assignment |
| Data | Synthetic data and sample services only. No real company systems |
| Secrets | No real cloud accounts, credentials, tokens or keys. Never commit secrets, not even fake-looking real ones |
| Tools | Docker, GitHub Actions, Terraform/OpenTofu are allowed. Equivalents are fine if you explain the choice |
| Cost | Everything must run locally or on free tiers. No mandatory paid infrastructure |
| AI use | Allowed, but you must explain, verify and own every line you submit |
| Submission | Submission window 3 calendar days, then a technical discussion |

## Each assignment folder contains

| File | Purpose |
|---|---|
| `README.md` | Overview (WH table), evaluation weights, reading list |
| `product-brief.md` | Start here. What you build: product, personas, journey, capabilities, user stories with acceptance criteria |
| `requirements-and-directives.md` | Part 1 requirements and scenarios. Part 2 do / don't rules, deliverables, constraints, discussion |
| `resources.md` | Reference links for the topic. Starting points, not solutions |
| `developer-guide.md` | Build order, directions, and before / during / after checklists |
