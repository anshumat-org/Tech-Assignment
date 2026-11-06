# Developer Instructions

**v1.0 — 2026-11-06** · Mandatory engineering principles for all five assignments

| # | Principle | Rule |
|---|---|---|
| 1 | Human-instructed development | Code is driven by explicit human requirements and decisions. Understand the task first. AI assistants may be used but must not invent product behaviour, change scope or make unrequested architectural decisions. Record assumptions. Clarify ambiguity instead of guessing |
| 2 | Human-approved changes | A human reviews and approves code before it is complete or merged. This includes AI-generated code, dependency additions, schema changes, API changes, security-sensitive logic and major refactors. The developer is accountable for correctness, privacy, security and maintainability. Run relevant tests and explain material changes |
| 3 | Codebase-first, reusable engineering | Inspect the structure and follow its conventions. Reuse existing components, utilities, hooks, services, types and patterns. Build reusable components for repeated behaviour. Keep business logic out of presentation. Avoid duplication, one-off hacks, needless abstractions and rewrites without a reason |

## What you should be able to demonstrate

- Explain what you implemented, why, and which requirements drove it.
- Identify AI-generated or reused code, and explain, verify and take responsibility for it.
- Show where reusable components or shared logic replace duplication.
- Make a small change without destabilising unrelated parts.
- Show tests, review decisions and a clean, understandable codebase.

**Core principle:** AI can assist implementation. Humans own the instructions, approval and quality.

## Related

- [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md) for deliverable formats (including the AI usage disclosure in the README).
