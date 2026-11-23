# Frontend / Web Assignments

**v0.4 DRAFT — 2026-11-23**

| # | Assignment | Focus | Effort | Review | Folder |
|---|---|---|---|---|---|
| 01 | Accessible Component Library | Design tokens, a11y, keyboard, states, tests | 4–6 h | 30 min | [01-accessible-component-library](01-accessible-component-library/README.md) |
| 02 | Data Table & Search App | Mocked API, filters, URL state, performance | 6–8 h | 30–45 min | [02-data-table-search-app](02-data-table-search-app/README.md) |
| 03 | Multi-Step Form with Autosave | Validation, autosave, resume, network recovery | 5–7 h | 30–45 min | [03-multi-step-form-autosave](03-multi-step-form-autosave/README.md) |

**Choose any one assignment below and complete only that one.** Not sure? 01 is the smallest (fundamentals), 02 suits data-heavy UI, 03 suits forms and resilience.

## Tech stack

Any framework. TypeScript preferred. Mock APIs only; no secrets or real endpoints in client code.

| # | Language / framework | Database / storage | Tools, mocks and hosting | Flexibility |
|---|---|---|---|---|
| 01 | Any framework, TypeScript preferred | Not needed | Design tokens (shared or your own); headless libraries only if you can explain them | Any framework |
| 02 | Any framework, TypeScript preferred | Mock API data: 5,000+ synthetic rows from a seed script | MSW, json-server or similar | Any framework; works at 360 px and by keyboard |
| 03 | Any framework, TypeScript preferred | Mock API (drafts saved server-side) | MSW, json-server or similar; shared schema (for example Zod) | Any framework; works at 360 px and by keyboard |

## Rules for candidates

- Complete only the assignment selected for you.
- Read [frontend-instructions.md](frontend-instructions.md) first. It applies to every assignment.
- Mocked API and synthetic data only (for example MSW or json-server). No real services, no secrets in client code.
- Use any framework. TypeScript preferred.
- Start from [../shared/design-system/README.md](../shared/design-system/README.md) tokens, or document your own.
- Submission window 3 calendar days, then a technical discussion.
- Follow [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md).

## Each assignment folder contains

| File | Purpose |
|---|---|
| `README.md` | Overview, WH table, evaluation weights |
| `product-brief.md` | Start here. What you build: product, personas, journey, capabilities, user stories with acceptance criteria |
| `requirements-and-directives.md` | Part 1 requirements and scenarios. Part 2 do / don't rules, deliverables, constraints, discussion |
| `resources.md` | Reference links for the topic. Starting points, not solutions |
| `developer-guide.md` | Build order, directions, and before / during / after checklists |
