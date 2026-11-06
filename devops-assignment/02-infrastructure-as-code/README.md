# Assignment 02 — Infrastructure as Code

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | IaC for two environments (staging and production) of a small sample service, with secrets handling and least-privilege access |
| Why | Tests repeatable infrastructure, safe change review and permission design |
| Who | A DevOps engineer who provisions and maintains environments |
| How | Terraform or OpenTofu preferred, equivalents allowed. Local providers, containers or mocked cloud tools (for example LocalStack). Reuse modules across environments |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Runs locally. No real cloud account or paid resources. Plan output is acceptable where apply is impossible |
| Which | Second assignment of the DevOps track, after 01. Can stand alone |

## Evaluation weights

| Area | Weight |
|---|---|
| Module structure and environment separation | 20% |
| Reproducibility from clean state | 20% |
| Secrets handling | 20% |
| Least-privilege access design | 20% |
| Change safety (plan review, drift, rollback) | 10% |
| Documentation and explanation | 10% |
| **Total** | **100%** |

## Read next

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../README.md](../README.md) (track index)
- [../devops-instructions.md](../devops-instructions.md) (mandatory for every assignment)
