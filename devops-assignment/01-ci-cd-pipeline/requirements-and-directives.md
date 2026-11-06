# Assignment 01 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Sample service
- A small HTTP service with a health endpoint, a version endpoint and at least three unit tests.
- Synthetic logic only. A Dockerfile that builds a small, non-root image.

### B. Pipeline stages

| Stage | Minimum expectation |
|---|---|
| Build | Reproducible build, pinned base image and dependencies, cached where safe |
| Test | Unit tests run on every push and pull request. Fail fast |
| Security scan | Dependency scan and image or config scan. Define which severities block |
| Package | Image tagged by commit SHA, not only `latest` |
| Deploy to staging | Automatic on merge to main, followed by a smoke test |
| Promote | Same artifact moves to production behind a manual approval. No rebuild |
| Rollback | Documented and tested path to the previous version |

### C. Pipeline hygiene
- Pipeline defined as code in the repo.
- Least-privilege tokens and permissions for each job.
- Secrets come from the CI secret store or placeholders. None in the repo.
- Clear failure output and a visible status for each stage.

### D. Engineering scenarios (answer in README)
- A scan finds a high-severity vulnerability on the release day. What happens?
- Staging passes but production fails the smoke test. What happens next?
- How do you guarantee the artifact promoted is the artifact tested?
- A secret is committed by mistake. What are your steps?
- Two merges land close together. How do you avoid a bad deploy order?
- How would you add a database migration safely?

### E. Rollback evidence
- Show a deploy of a deliberately broken version, detection, and rollback.
- State how long rollback takes and what it cannot undo.

### F. Live follow-up
The interviewer may ask you to add a new quality gate (for example a lint step or a coverage threshold) or change which scan severity blocks a release. Keep stages modular so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Keep the service and pipeline small and correct | Add Kubernetes, service mesh or multi-region setups |
| Build once, promote the same artifact | Rebuild per environment |
| Pin versions and tag by commit SHA | Rely on `latest` tags |
| Set minimal job permissions and use a secret store | Use broad tokens or hard-coded credentials |
| Gate production behind approval and a smoke test | Auto-deploy to production without checks |
| Document and rehearse rollback | Assume rollback works |
| Record assumptions and explain AI-assisted parts | Submit configuration you cannot explain |

### Deliverables

| Item | Detail |
|---|---|
| Git repo with sample service, Dockerfile, pipeline files | Setup instructions and meaningful commits |
| Pipeline run evidence | Logs or screenshots of a green run and a blocked run |
| Rollback evidence | Output of the broken-deploy and rollback exercise |
| One-page design note | Stage diagram (Mermaid welcome), gate rules, trade-offs |
| README | Assumptions, scenario answers (section D), known limits |

### Constraints
- Free tiers and local tools only. Any CI system and language.
- Synthetic data only. No real accounts, keys or tokens.
- Any environment is simulated. Say clearly what is simulated.
- AI assistance is allowed. You own the result ([../devops-instructions.md](../devops-instructions.md)).

### Technical discussion (30 min)
Walk through the pipeline, one gate you would tighten, and the rollback path. Explain what happens on a failed scan. Expect a live change to a gate. Show the dry-run or plan output before any apply.
