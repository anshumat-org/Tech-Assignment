# Frontend / Web Developer Instructions

**v0.1 DRAFT — 2026-11-06** · Mandatory engineering principles for all Frontend / Web assignments. Assignments: see the track README.

| # | Principle | Rule |
|---|---|---|
| 1 | Human-instructed development | Code is driven by explicit human requirements, designs and decisions. Understand the task and the design first. AI assistants may be used but must not invent product behaviour, change scope or make unrequested architectural decisions. Record assumptions. Clarify ambiguity instead of guessing |
| 2 | Human-approved changes | A human reviews and approves code before it is complete or merged. This includes AI-generated code, dependency additions, API contract assumptions, accessibility behaviour, security-sensitive logic and major refactors. The developer is accountable for correctness, accessibility, performance and maintainability. Run relevant tests and explain material changes |
| 3 | Component-first and reusable | Inspect the existing structure and follow its conventions. Reuse existing components, hooks, utilities, types and design tokens. Build reusable components for repeated behaviour. Keep data fetching and business logic separate from presentation. Handle loading, empty, success and error states. Meet basic accessibility: keyboard use, labels, contrast, no colour-only meaning. Work on small screens. Never put secrets in client code. Avoid duplication, one-off hacks, needless libraries and rewrites without a reason |

## What you should be able to demonstrate

- Explain what you built, why, and which requirement or design drove it.
- Identify AI-generated or reused code, and explain, verify and take responsibility for it.
- Show reusable components and shared logic in place of duplication.
- Show all UI states for a key flow, including failure and empty.
- Show accessibility and responsive behaviour, and one performance decision.
- Make a small change without breaking unrelated screens.
- Show tests and review decisions.

**Core principle:** AI can assist implementation. Humans own the instructions, approval and quality.
