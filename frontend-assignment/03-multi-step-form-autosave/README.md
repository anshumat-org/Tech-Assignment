# Assignment 03 — Multi-Step Form with Autosave

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | A multi-step application form with schema validation, autosave, resume and recovery from network failure |
| Why | Tests form architecture, validation design, async resilience and accessibility in a realistic flow |
| Who | An applicant who fills a long form over several sittings, possibly on a poor connection |
| How | Any framework. TypeScript preferred. Shared schema (for example Zod). Mock API with MSW or json-server |
| When | 5–7 hours of effort. Review 30–45 minutes |
| Where | Runs locally, no paid infrastructure |
| Which | Frontend track, after 01 or as an alternative to 02 |

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

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../../shared/design-system/README.md](../../shared/design-system/README.md)
- [../frontend-instructions.md](../frontend-instructions.md) (mandatory for every assignment)
