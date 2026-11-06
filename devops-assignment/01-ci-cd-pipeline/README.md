# Assignment 01 — CI/CD Pipeline

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | A CI/CD pipeline for a small sample service: build, test, security scan, deploy to staging, promote to production, roll back |
| Why | Tests safe, repeatable delivery and rollback thinking. Staging and production may be simulated locally |
| Who | A DevOps engineer who owns delivery for a small team |
| How | Any sample service (a tiny HTTP API is fine, supplied or self-written). GitHub Actions preferred, equivalents allowed. Docker for packaging |
| When | 4–6 hours of effort. Review 30 minutes |
| Where | Runs on a free CI tier and locally. Deploy targets can be Docker Compose or a local cluster. No real cloud accounts |
| Which | Recommended first assignment of the DevOps track. Next is 02 |

## Evaluation weights

| Area | Weight |
|---|---|
| Pipeline design and stage ordering | 20% |
| Testing and quality gates | 15% |
| Security scanning and secrets handling | 20% |
| Deployment, promotion and rollback | 25% |
| Reproducibility and repo conventions | 10% |
| Documentation and explanation | 10% |
| **Total** | **100%** |

Tool choice is secondary to sound, explainable delivery practice.

## Read next

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../README.md](../README.md) (track index)
- [../devops-instructions.md](../devops-instructions.md) (mandatory for every assignment)
