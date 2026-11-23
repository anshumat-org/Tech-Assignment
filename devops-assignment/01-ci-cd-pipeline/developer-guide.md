# Assignment 01 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 4–6 hours on a safe, repeatable pipeline and a tested rollback, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Sample service: health and version endpoints, 3+ unit tests, non-root Dockerfile | Tests pass locally. Image builds and runs | 0.75 h |
| 2 | Build and test stages | Runs on every push and PR. Pinned base image and dependencies. Fails fast | 0.75 h |
| 3 | Security scan stage | Dependency scan and image or config scan run. Blocking severities are stated | 0.75 h |
| 4 | Package | Image tagged by commit SHA, not only `latest` | 0.5 h |
| 5 | Deploy to staging and smoke test | Merge to main deploys automatically, then the smoke test runs | 1 h |
| 6 | Promote to production | Same artifact moves behind a manual approval. No rebuild | 0.75 h |
| 7 | Rollback and evidence | Deliberately broken version is detected and rolled back. Time to roll back is noted | 0.75 h |
| 8 | Design note, scenario answers, README | Checklist C is complete | 0.75 h |

Get one stage green end to end first. Add the next stage only when the last one works.

## 2. Directions

| Topic | Direction |
|---|---|
| Scope | Keep the service and pipeline small and correct. No Kubernetes, service mesh or multi-region |
| Build once | Build one artifact and promote that same artifact. Never rebuild per environment |
| Versions | Pin base image and dependencies. Tag by commit SHA |
| Gates | Say which scan severities block a release. Keep each stage modular so a gate is a small change |
| Permissions | Set minimal permissions per job. Use the CI secret store or placeholders |
| Production | Gate behind a manual approval and a smoke test |
| Rollback | Document it and rehearse it. State how long it takes and what it cannot undo |
| Simulation | Staging and production may be simulated locally. State clearly what is simulated |
| Apply | Show the dry-run or plan output before any apply ([../devops-instructions.md](../devops-instructions.md)) |
| AI use | Allowed. Record it. Explain, verify and own every line |
| Scope gaps | If you skip something, list it under known limits in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../devops-instructions.md](../devops-instructions.md) and [../README.md](../README.md)
- [ ] Confirm you are doing Assignment 01 (not another one)
- [ ] Choose CI tool (GitHub Actions preferred) and deploy target (Docker Compose or local cluster). Note any change and why
- [ ] Verify Docker and your language runtime work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Use synthetic logic only. No real cloud accounts, keys or tokens
- [ ] Sketch the stage diagram and gate rules (Mermaid is fine)
- [ ] Write down assumptions and what is simulated
- [ ] Plan the 8 steps above against your available hours
- [ ] Read the six scenarios in section D so your design can answer them

## 4. Checklist B — While developing

### Service and image
- [ ] Health endpoint and version endpoint work
- [ ] At least three unit tests pass
- [ ] Image is small and runs as non-root
- [ ] Base image and dependencies are pinned

### Pipeline stages
- [ ] Pipeline is defined as code in the repo
- [ ] Unit tests run on every push and pull request
- [ ] Dependency scan and image or config scan run, with blocking severities defined
- [ ] Image is tagged by commit SHA
- [ ] Merge to main deploys to staging, then a smoke test runs
- [ ] Production promotion uses the same artifact, behind manual approval
- [ ] Each stage has clear failure output and a visible status

### Security
- [ ] Each job has least-privilege permissions
- [ ] Secrets come from the CI secret store or placeholders. None in the repo
- [ ] No secrets in logs or workflow output
- [ ] You can state your steps if a secret is committed by mistake

### Rollback
- [ ] A broken version is deployed on purpose and detected
- [ ] Rollback to the previous version works and is documented
- [ ] Rollback time and its limits (for example data or migrations) are written down

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go
- [ ] Review the dry-run or plan output before applying any change

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Build, test, scan, deploy to staging. All work
- [ ] You have a green run and a blocked run (for example a failed scan or test)
- [ ] Promoted artifact is provably the one tested (same SHA or digest)
- [ ] Rollback rehearsal repeated from a clean state
- [ ] Live-change rehearsal: add a lint step or change which scan severity blocks, in a small diff

### Deliverables
- [ ] Git repo with sample service, Dockerfile and pipeline files, with setup instructions
- [ ] Pipeline run evidence: logs or screenshots of a green run and a blocked run
- [ ] Rollback evidence: output of the broken-deploy and rollback exercise
- [ ] One-page design note: stage diagram, gate rules, trade-offs
- [ ] README contains: assumptions, what is simulated, answers to scenarios in section D, known limits, AI usage disclosure

### Hygiene
- [ ] No secrets, `.env` or tokens in git history
- [ ] No dead config, commented-out stages or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit within 3 calendar days via the route given in the root README

### Prepare for the discussion (30 min)
- [ ] Can walk through every stage and why it is in that order
- [ ] Can explain one gate you would tighten
- [ ] Can explain what happens on a failed scan and on a failed production smoke test
- [ ] Can explain the rollback path and what it cannot undo
- [ ] Ready to change a gate live and show the dry-run before apply

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Rebuilding the image for production | Build once, promote the same artifact |
| Using `latest` as the only tag | Tag by commit SHA |
| Broad tokens or hard-coded credentials | Minimal job permissions and the secret store |
| Auto-deploying to production | Manual approval plus smoke test |
| Rollback written but never run | Rehearse it and record the time |
| Scan severities left undefined | State what blocks a release |
| Pipeline monolith that is hard to change | Modular stages, so a new gate is a small change |
| Elaborate tooling, thin explanations | Small pipeline you can fully explain |
