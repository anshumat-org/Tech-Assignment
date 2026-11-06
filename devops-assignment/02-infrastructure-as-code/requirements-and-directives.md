# Assignment 02 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Environments

| Item | Staging | Production |
|---|---|---|
| Purpose | Pre-release verification | Serves users (simulated) |
| Size | Minimal | Larger or replicated, in variables only |
| Change flow | Apply after review | Apply after review plus explicit approval |
| Data | Synthetic | Synthetic, treated as sensitive |

- One shared module, per-environment variable files. No copy-pasted environment code.
- Minimum resources: network or isolation boundary, a compute target for the sample service, a data store, and an identity per workload.

### B. State and reproducibility
- Remote or local state with a documented backend choice and locking behaviour.
- One documented command sequence rebuilds each environment from a clean checkout.
- Re-running apply makes no changes (idempotent). Show the empty plan.

### C. Secrets
- No secrets in code, state examples, logs or variable defaults.
- Use a secrets manager (real or simulated) and inject at runtime.
- Document rotation and what happens on a leaked secret.

### D. Least privilege
- A separate identity for the pipeline, the workload and a human operator.
- Policies list explicit actions and resources. No wildcards without a written reason.
- Production permissions are narrower than staging for humans.

### E. Engineering scenarios (answer in README)
- Someone changes a resource in the console. How do you detect and handle drift?
- A plan shows a resource will be destroyed and recreated. What do you do?
- State is lost or corrupted. How do you recover?
- How do you roll out a change to staging first, then production?
- A teammate needs temporary production access. How is it granted and revoked?
- How do you estimate and cap cost?

### F. Live follow-up
The interviewer may ask you to add a third environment or a new service identity with narrowly scoped access, then show the plan. Structure modules so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Use one module with per-environment variables | Duplicate code between environments |
| Show the plan and review it before apply | Apply without reading the plan |
| Keep state and secrets out of the repo | Commit state files, keys or `.tfvars` with secrets |
| Scope each identity to specific actions and resources | Use admin or wildcard permissions for convenience |
| Make apply idempotent and document the clean rebuild | Rely on manual console steps |
| Tag resources and document cost assumptions | Create unbounded or paid resources |
| Document rollback and destroy safeguards | Add destroy-prone changes without a warning |

### Deliverables

| Item | Detail |
|---|---|
| Git repo with modules, environment configs, README | Setup instructions and meaningful commits |
| Plan output | Staging and production plans, plus an empty re-run plan |
| Access matrix | Identity, purpose, permissions, environment |
| Secrets note | Source, injection, rotation, leak response |
| One-page design note | Diagram (Mermaid welcome), state strategy, trade-offs |
| Scenario answers | Section E in the README |

### Constraints
- Terraform or OpenTofu preferred. Equivalents allowed with a short reason.
- Local or mocked providers only. No real accounts, keys or paid resources.
- Synthetic data only.
- AI assistance allowed. A human approves every change ([../devops-instructions.md](../devops-instructions.md)).

### Technical discussion (30–45 min)
Rebuild one environment live from a clean checkout. Walk through the access matrix and one risky plan change. Explain recovery from lost state. Expect a live permission or environment change, shown as a plan before apply.
