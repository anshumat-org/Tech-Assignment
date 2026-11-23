# Full-Stack Assignment

**v1.4 — 2026-11-23** · Tech stack section added. "Choose any one assignment" rule and checklist section added. v1.2 added Assignment 06, product briefs and developer guides.

> **Choose any one assignment from the table below and complete only that one.** Do not submit more than one. Pick the one that best shows your strengths.

| # | Assignment | Best for | Focus | Effort | Folder |
|---|---|---|---|---|---|
| 01 | Assessment & Intelligence Platform | Backend, SQL, data engineering | DB design, SQL, allocation engine, scoring | 8–12 h | [01-assessment-intelligence-platform](01-assessment-intelligence-platform/README.md) |
| 02 | AI-Powered Daily Knowledge System | Product, frontend, local-first, AI apps | Outliner UX, offline sync, AI extraction | 8–12 h | [02-ai-daily-knowledge-system](02-ai-daily-knowledge-system/README.md) |
| 03 | Mini Workflow Engine | Fundamentals, shortest option | Code quality, transactions, API design | 3–4 h | [03-mini-workflow-engine](03-mini-workflow-engine/README.md) |
| 04 | Passport Application & Tracking (DigiLocker) | Integrations, security, workflows | State machine, consent, adapters, audit trail | 6–8 h | [04-passport-application-tracking](04-passport-application-tracking/README.md) |
| 05 | Chat-First Inventory & Billing | Commerce, conversational apps | Chat-to-action, inventory ledger, bilingual UX, reports | 8–10 h | [05-chat-first-inventory-billing](05-chat-first-inventory-billing/README.md) |
| 06 | Mandi Munshi: Digital Hal Khata | Fintech, ledgers, accounting logic | Double-entry ledger, settlement, reversals, reports | 8–10 h | [06-mandi-munshi-hal-khata](06-mandi-munshi-hal-khata/README.md) |

**How to choose**

| If you are strongest in… | Choose |
|---|---|
| Backend, SQL, data modelling | 01 |
| Product UX, offline-first, AI features | 02 |
| Clean fundamentals, limited time | 03 |
| Integrations, security, consent, workflows | 04 |
| Commerce, chat interfaces, bilingual apps | 05 |
| Ledgers, money correctness, accounting logic | 06 |

## Tech stack

Preferred choices come from each assignment's constraints. You may use something else: justify major choices in your README.

| # | Language / framework | Database / storage | Tools, mocks and hosting | Flexibility |
|---|---|---|---|---|
| 01 | TypeScript, Node.js backend, React or Next.js frontend | PostgreSQL (SQLite acceptable) | Docker optional. Runs locally | TypeScript where practical; justify major choices |
| 02 | TypeScript, React or Next.js PWA, Node.js API | IndexedDB on the device, PostgreSQL on the server | Provider-independent AI service, mock AI if no key | TypeScript where practical; no paid infrastructure required |
| 03 | Any language and framework, TypeScript preferred | Relational database: PostgreSQL preferred, SQLite acceptable | None required | Any stack; keep it small |
| 04 | TypeScript preferred | PostgreSQL preferred | DigiLocker adapter with a mock implementation | Mock provider expected without authorised credentials |
| 05 | TypeScript preferred | PostgreSQL preferred | Chat or LLM adapter, mock or deterministic parser if no AI key | Must work without an AI key |
| 06 | TypeScript preferred | PostgreSQL preferred (integer paise or decimal for money) | No real payment integration; voice or photo input optional | Runs locally from a clean clone |

**Rules for candidates**
- Choose any one assignment and complete only that one.
- Read [developer-instructions.md](developer-instructions.md). It applies to every assignment.
- Submission window 3 calendar days, then a technical discussion (20–45 min, depending on the assignment).
- Use synthetic data. Do not reproduce OnRole production systems.
- Follow [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md) and submit via the form linked in the root README.

## Checklist

Tick these for the one assignment you chose. Your assignment's `developer-guide.md` has the detailed, assignment-specific version.

### Before you start
- [ ] Choose one assignment and note its expected effort
- [ ] Read, in order: `product-brief.md` → `requirements-and-directives.md` → `developer-guide.md` → `design-system/README.md` → `samples/`
- [ ] Read [developer-instructions.md](developer-instructions.md) and [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md)
- [ ] Write down your assumptions where the brief is silent
- [ ] Choose your stack (TypeScript and PostgreSQL preferred); note and justify any change
- [ ] Check your runtime, database and package manager work locally
- [ ] Create the repo with a README skeleton and `.gitignore`; no `.env` or secrets committed
- [ ] Sketch the HLD and ER diagram before coding
- [ ] Map the build order in `developer-guide.md` to your available hours
- [ ] List the tests the brief requires and plan synthetic seed data

### While developing
- [ ] Build core logic and data model first; UI polish last
- [ ] Trace every feature to a user story in `product-brief.md`
- [ ] Validate all input server-side and return consistent errors
- [ ] Enforce access and scope on the server, never from client-sent IDs or roles
- [ ] Use DB transactions and make retries safe (idempotency) wherever data is written
- [ ] Match the screens in `product-brief.md` and their `samples/` for look and feel
- [ ] Write tests with each build step, not at the end
- [ ] Commit small and often with meaningful messages
- [ ] Keep a running list of assumptions, shortcuts and AI tool use
- [ ] No secrets, tokens or real personal data in code, logs or seed data

### After developing (before you submit)
- [ ] Fresh clone: follow your own README exactly; setup, seed, run and test all work
- [ ] All required tests pass and cover the brief's named scenarios
- [ ] Each user story's acceptance criteria can be shown working
- [ ] Deliverables present: HLD, ER diagram, schema, API docs, demo (per `SUBMISSION_FORMATS.md`)
- [ ] README has setup, assumptions, trade-offs, limitations, future work, AI usage disclosure and sources
- [ ] Rehearse the live follow-up change described in your brief
- [ ] Submit within 3 calendar days via the form

**Each assignment folder contains**

| File / folder | Purpose |
|---|---|
| `README.md` | Overview, scope, what is evaluated |
| `product-brief.md` | Start here. Product, personas, journey, capabilities, features, screens, configuration, user stories with acceptance criteria |
| `requirements-and-directives.md` | Part 1 requirements and scenarios. Part 2 do / don't rules, deliverables, constraints, discussion |
| `resources.md` | Reference links for the topic. Starting points, not solutions |
| `developer-guide.md` | Build order, directions, and before / during / after checklists |
| `design-system/` | UI guidance specific to this assignment |
| `samples/` | Wireframe images for each screen, showing the expected look and feel (not solutions) |
