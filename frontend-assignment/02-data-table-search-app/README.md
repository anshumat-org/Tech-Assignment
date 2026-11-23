# Assignment 02 — Data Table & Search App

**v0.3 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | A data-heavy table and search app over a mocked API, with filters, sorting, paging or virtualization and URL-synced state |
| Why | Tests state management, async handling, performance reasoning and resilient UI at realistic data size |
| Who | An analyst or operator who searches, narrows and shares views of a large record list |
| How | Any framework. TypeScript preferred. Mock API with MSW or json-server, 5,000+ synthetic rows |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Runs locally, no paid infrastructure |
| Which | Frontend track, after 01 or as an alternative to 03 |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Language | TypeScript preferred | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/typescript/typescript-original.svg" alt="TypeScript" title="TypeScript" height="32"> |
| Framework | Any framework | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/react/react-original.svg" alt="React" title="React (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/vuejs/vuejs-original.svg" alt="Vue" title="Vue (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/svelte/svelte-original.svg" alt="Svelte" title="Svelte (example)" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/angularjs/angularjs-original.svg" alt="Angular" title="Angular (example)" height="32"> |
| Data | Mock API, 5,000+ synthetic rows from a seed script | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/javascript/javascript-original.svg" alt="Seed script" title="Seed script" height="32"> |
| Mocking | MSW, json-server or similar | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/nodejs/nodejs-original.svg" alt="Node.js" title="Mock server" height="32"> |

## Evaluation weights

| Area | Weight |
|---|---|
| State and data fetching design | 25% |
| URL-synced state and navigation | 15% |
| Performance reasoning and implementation | 20% |
| Loading, empty and error states | 15% |
| Accessibility and responsive layout | 10% |
| Testing | 10% |
| Code structure and README trade-offs | 5% |
| **Total** | **100%** |

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../../shared/design-system/README.md](../../shared/design-system/README.md)
- [../frontend-instructions.md](../frontend-instructions.md) (mandatory for every assignment)
