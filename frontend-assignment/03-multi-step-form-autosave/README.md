# Assignment 03 — Multi-Step Form with Autosave

**v0.3 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | A multi-step application form with schema validation, autosave, resume and recovery from network failure |
| Why | Tests form architecture, validation design, async resilience and accessibility in a realistic flow |
| Who | An applicant who fills a long form over several sittings, possibly on a poor connection |
| How | Any framework. TypeScript preferred. Shared schema (for example Zod). Mock API with MSW or json-server |
| When | 5–7 hours of effort. Review 30–45 minutes |
| Where | Runs locally, no paid infrastructure |
| Which | Frontend track, after 01 or as an alternative to 02 |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Language | TypeScript preferred | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/typescript/typescript-original.svg" alt="TypeScript" title="TypeScript" height="32"> |
| Framework | Any framework | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/react/react-original.svg" alt="React" title="React (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/vuejs/vuejs-original.svg" alt="Vue" title="Vue (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/svelte/svelte-original.svg" alt="Svelte" title="Svelte (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/angularjs/angularjs-original.svg" alt="Angular" title="Angular (example)" height="32"> |
| Validation | Shared schema (for example Zod) | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/typescript/typescript-original.svg" alt="Schema" title="Shared schema" height="32"> |
| Mocking | MSW or json-server. Drafts saved server-side | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/nodejs/nodejs-original.svg" alt="Node.js" title="Mock server" height="32"> |

## Evaluation weights

| Area | Weight |
|---|---|
| Form architecture and schema validation | 20% |
| Autosave, resume and conflict handling | 20% |
| Network failure and server-error handling | 20% |
| Accessibility (errors, focus, steps) | 15% |
| Testing | 10% |
| Responsive layout and UI states | 10% |
| Code structure and README trade-offs | 5% |
| **Total** | **100%** |

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../../shared/design-system/README.md](../../shared/design-system/README.md)
- [../frontend-instructions.md](../frontend-instructions.md) (mandatory for every assignment)
