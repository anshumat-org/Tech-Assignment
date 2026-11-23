# Assignment 02 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on module design, secrets and least privilege, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Tool setup, state backend choice, repo skeleton | Init works locally. Backend and locking behaviour are noted | 0.75 h |
| 2 | One shared module: isolation boundary, compute target, data store, identity per workload | Module plans cleanly with variables only | 1.5 h |
| 3 | Staging and production variable files | Both environments plan from the same module. No copied code | 1 h |
| 4 | Secrets handling | Secrets come from a secrets manager (real or simulated) and are injected at runtime. None in code or defaults | 1 h |
| 5 | Identities and policies | Separate pipeline, workload and human operator identities. Explicit actions and resources | 1.25 h |
| 6 | Clean rebuild and idempotency | Documented command sequence rebuilds each environment. Re-apply shows an empty plan | 1 h |
| 7 | Change safety: drift, destroy-recreate warning, rollback | Scenario answers drafted. Destroy safeguards documented | 0.75 h |
| 8 | Access matrix, secrets note, design note, README | Checklist C is complete | 0.75 h |

Get staging working from a clean checkout first. Production is then a variable change.

## 2. Directions

| Topic | Direction |
|---|---|
| Modules | One shared module with per-environment variable files. Do not duplicate environment code |
| Environments | Staging is minimal. Production is larger or replicated, in variables only |
| Plan first | Show the plan and review it before every apply |
| State | Document the backend and locking. Keep state files out of the repo |
| Reproducibility | One documented command sequence rebuilds each environment from a clean checkout |
| Idempotency | Re-running apply makes no changes. Show the empty plan |
| Secrets | No secrets in code, state examples, logs or variable defaults. Inject at runtime. Document rotation and leak response |
| Least privilege | List explicit actions and resources. No wildcards without a written reason. Production human access is narrower than staging |
| Cost | Tag resources and document cost assumptions. No unbounded or paid resources |
| Providers | Local or mocked only (for example LocalStack or containers). Plan output is acceptable where apply is impossible |
| Change flow | Staging: apply after review. Production: review plus explicit approval |
| AI use | Allowed. A human approves every change. Record usage ([../devops-instructions.md](../devops-instructions.md)) |
| Scope gaps | If you skip something, list it under known limits in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../devops-instructions.md](../devops-instructions.md) and [../README.md](../README.md)
- [ ] Confirm you are doing Assignment 02 (not another one)
- [ ] Choose tool (Terraform or OpenTofu preferred) and local or mocked provider. Note any change and why
- [ ] Verify the tool, Docker (if used) and the mock provider work locally
- [ ] Create a new git repo with a README skeleton and a `.gitignore` covering state files, `.tfvars` with secrets and `.env`
- [ ] No real cloud account, keys or paid resources. Synthetic data only
- [ ] Sketch the environment diagram and state strategy (Mermaid is fine)
- [ ] Draft the access matrix: identity, purpose, permissions, environment
- [ ] Write down assumptions
- [ ] Plan the 8 steps above against your available hours
- [ ] Read the six scenarios in section E so your design can answer them

## 4. Checklist B — While developing

### Modules and environments
- [ ] One shared module, per-environment variable files
- [ ] Staging and production differ in variables only
- [ ] Minimum resources present: isolation boundary, compute target, data store, identity per workload
- [ ] Resources are tagged

### State and reproducibility
- [ ] Backend choice and locking behaviour are documented
- [ ] No state files or `.tfvars` with secrets in git
- [ ] Rebuild from a clean checkout works with the documented sequence
- [ ] Second apply produces an empty plan

### Secrets
- [ ] No secrets in code, state examples, logs or variable defaults
- [ ] Secrets injected at runtime from a secrets manager (real or simulated)
- [ ] Rotation and leaked-secret steps are written down

### Least privilege
- [ ] Separate identities for pipeline, workload and human operator
- [ ] Policies list explicit actions and resources. Any wildcard has a written reason
- [ ] Production human permissions are narrower than staging

### Change safety
- [ ] Plan read and understood before each apply
- [ ] Destroy-and-recreate changes are flagged with a warning
- [ ] Rollback and destroy safeguards are documented

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Init, plan, apply for each environment. All work
- [ ] Staging plan, production plan and an empty re-run plan are saved as evidence
- [ ] Search the repo and history for keys, tokens and state files. None found
- [ ] Live-change rehearsal: add a third environment or a new, narrowly scoped service identity, and show the plan

### Deliverables
- [ ] Git repo with modules, environment configs and README, with setup instructions
- [ ] Plan output: staging, production and empty re-run
- [ ] Access matrix: identity, purpose, permissions, environment
- [ ] Secrets note: source, injection, rotation, leak response
- [ ] One-page design note: diagram, state strategy, trade-offs
- [ ] README contains: assumptions, answers to scenarios in section E, known limits, AI usage disclosure

### Hygiene
- [ ] No secrets, state or `.env` in git history
- [ ] No dead code, unused variables or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit within 3 calendar days via the route given in the root README

### Prepare for the discussion (30–45 min)
- [ ] Can rebuild one environment live from a clean checkout
- [ ] Can walk through the access matrix
- [ ] Can explain one risky plan change and how you would handle it
- [ ] Can explain recovery from lost or corrupted state
- [ ] Ready for a live permission or environment change, shown as a plan before apply

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Copy-pasted code per environment | One module, variable files |
| Applying without reading the plan | Review the plan first. Flag destroy-recreate |
| Committing state, keys or `.tfvars` with secrets | Ignore them. Use a secrets manager |
| Admin or wildcard permissions for convenience | Explicit actions and resources per identity |
| Same human access in staging and production | Narrower production permissions |
| Manual console steps in the rebuild | Everything in code and documented commands |
| No proof of idempotency | Save the empty re-run plan |
| Unbounded or untagged resources | Tag and state cost assumptions |
