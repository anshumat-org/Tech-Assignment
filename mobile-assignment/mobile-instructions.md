# Mobile App Developer Instructions

**v0.1 DRAFT — 2026-11-06** · Mandatory engineering principles for all Mobile App assignments. Assignments: see the track README.

| # | Principle | Rule |
|---|---|---|
| 1 | Human-instructed development | Code is driven by explicit human requirements, designs and decisions. Understand the task, the target platforms and the users first. AI assistants may be used but must not invent product behaviour, change scope or make unrequested architectural decisions. Record assumptions. Clarify ambiguity instead of guessing |
| 2 | Human-approved changes | A human reviews and approves code before it is complete or merged. This includes AI-generated code, dependency additions, permission requests, local data storage, security-sensitive logic, API contract assumptions and major refactors. The developer is accountable for correctness, privacy, security, performance and maintainability. Run relevant tests and explain material changes |
| 3 | Platform-aware, resilient and reusable | Follow the existing structure and the platform's conventions. Reuse existing components, services and types. Keep UI, business logic, storage and networking separate. Design for poor or no connectivity, interruptions and app restarts. Request the fewest permissions needed, and only when needed. Store sensitive data in secure storage and never ship secrets in the app bundle. Respect battery, memory and small or varied screens. Support accessibility such as screen readers and text scaling. Avoid duplication, one-off hacks, needless libraries and rewrites without a reason |

## What you should be able to demonstrate

- Explain what you built, why, and which requirement drove it.
- Identify AI-generated or reused code, and explain, verify and take responsibility for it.
- Show behaviour when offline, on a slow network, and after the app is killed and reopened.
- Show which permissions are requested, when, and what happens if the user refuses.
- Show where sensitive data is stored and what is deliberately not stored.
- Show reusable components, and behaviour on at least two screen sizes.
- Make a small change without breaking unrelated screens.
- Show tests and review decisions.

**Core principle:** AI can assist implementation. Humans own the instructions, approval and quality.
