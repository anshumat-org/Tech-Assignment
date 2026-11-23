# Assignment 01 — Assessment & Intelligence Platform

**v1.2 — 2026-11-23**

| WH | Answer |
|---|---|
| What | A configurable assessment platform: question bank, blueprints, allocation engine, attempt execution, scoring |
| Why | Tests whether you can design an assessment engine on a sound relational model, not just a questionnaire UI |
| Who | Admins manage questions and assessments. Candidates take attempts |
| How | TypeScript, Node.js backend, PostgreSQL (SQLite acceptable), React or Next.js frontend |
| When | 8–12 hours of effort, 3 calendar day window |
| Where | Runs locally, no mandatory paid infrastructure |
| Which | Two assessment types: technical and psychometric |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Language | TypeScript where practical | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/typescript/typescript-original.svg" alt="TypeScript" title="TypeScript" height="32"> |
| Backend | Node.js | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/nodejs/nodejs-original.svg" alt="Node.js" title="Node.js" height="32"> |
| Frontend | React or Next.js | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/react/react-original.svg" alt="React" title="React" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/nextjs/nextjs-original.svg" alt="Next.js" title="Next.js" height="32"> |
| Database | PostgreSQL (SQLite acceptable) | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" title="PostgreSQL" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/sqlite/sqlite-original.svg" alt="SQLite" title="SQLite" height="32"> |
| Tools | Docker optional. Runs locally | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/docker/docker-original.svg" alt="Docker" title="Docker (optional)" height="32"> |

## Assessment types

| Technical | Psychometric |
|---|---|
| SQL and multiple-choice | Likert-scale |
| Single and multiple answer | Situational judgment |
| Topics, skills, difficulty | Competency dimensions |
| Correct answers and marks | Dimension mapping and reverse scoring |

## Evaluation weights

| Area | Weight |
|---|---|
| Database design and SQL | 25% |
| Backend architecture | 20% |
| Question allocation engine | 20% |
| Assessment execution and UI | 15% |
| Evaluation and scoring | 10% |
| Code quality and testing | 10% |

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [design-system/README.md](design-system/README.md)
- [samples/](samples/)
- [../developer-instructions.md](../developer-instructions.md) (mandatory for every assignment)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
