# Assignment 04 — Passport Application & Tracking with DigiLocker

**v1.3 — 2026-11-23**

| WH | Answer |
|---|---|
| What | A passport-assistance workflow app: applicant profile, document checklist, consent-led DigiLocker flow (mock), operator review, status timeline, notifications, audit trail |
| Why | Tests workflow and state-machine modelling, secure document handling, third-party integration boundaries, consent and auditability |
| Who | Applicants prepare and track an application. Operators review and decide |
| How | TypeScript preferred. PostgreSQL preferred. Adapter interfaces with mock implementations |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Runs locally. No real credentials or real personal data |
| Which | Integration and security depth. Used after the Assignment 03 screen |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Language | TypeScript preferred | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/typescript/typescript-original.svg" alt="TypeScript" title="TypeScript" height="32"> |
| Database | PostgreSQL preferred | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" title="PostgreSQL" height="32"> |
| Integration | DigiLocker adapter with a mock implementation. No real credentials | — |

## Important boundary

| Rule | Detail |
|---|---|
| Not the official system | The product helps organise and track an application. It must not pretend to be the Government of India's passport submission system |
| No production access assumed | Production DigiLocker and Passport Seva APIs are not available. Use an adapter interface and a clearly labelled mock unless you are given authorised sandbox credentials and API docs |
| Label simulated data | Simulated submission and tracking data is clearly marked as simulated |
| Never | Scrape government portals. Ask users for DigiLocker passwords, OTPs or authentication secrets |

## Evaluation weights

| Area | Weight |
|---|---|
| Data modelling and workflow / state machine | 20% |
| Backend / API design and validation | 20% |
| Security, privacy, consent and auditability | 20% |
| DigiLocker adapter / integration simulation | 15% |
| Frontend and tracking experience | 15% |
| Tests, documentation and code quality | 10% |

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [design-system/README.md](design-system/README.md)
- [../developer-instructions.md](../developer-instructions.md) (mandatory for every assignment)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
