# DevOps Instructions

**v0.1 DRAFT — 2026-11-06** · Mandatory engineering principles for all DevOps assignments. Assignments: see the track README.

| # | Principle | Rule |
|---|---|---|
| 1 | Human-instructed operations | Infrastructure and pipeline work is driven by explicit human requirements and decisions. Understand the task and the target environment first. AI assistants may be used but must not invent environments, architecture, scope or cost decisions. Record assumptions. Clarify ambiguity instead of guessing |
| 2 | Human-approved changes | A human reviews and approves infrastructure-as-code, pipeline changes, IAM and permission changes, secrets handling, network rules, cost-impacting changes and any destructive action before it is applied. Review the plan or dry-run output first. Document rollback. The engineer is accountable for security, reliability and cost. Run relevant checks and explain material changes |
| 3 | Repo-first, reproducible, least-privilege | Follow existing conventions and reuse existing modules, pipelines and scripts. Prefer code over manual console changes. Make changes repeatable and idempotent. Grant least privilege. Never commit secrets. Add monitoring and alerts for what you build. Avoid one-off hacks, needless tooling and rewrites without a reason |

## What you should be able to demonstrate

- Explain what you changed, why, and which requirement drove it.
- Identify AI-generated or reused configuration, and explain, verify and take responsibility for it.
- Rebuild the environment from a clean state using only the repo and documented steps.
- Show the plan or dry-run before apply, and show how to roll back.
- Show secrets handling, least-privilege access, and where logs and alerts live.
- Make a small change without destabilising unrelated services.

**Core principle:** AI can assist implementation. Humans own the instructions, approval and production safety.
