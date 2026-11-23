# Assignment 01 — Offline-First Notes App

**v0.3 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | A notes (or tasks) app that works fully offline, queues changes and syncs them to a mocked backend |
| Why | Tests resilience thinking: local persistence, retries, conflicts and recovery after the app is killed |
| Who | A user who writes notes on a train, in a lift or on a weak connection |
| How | React Native, Flutter, Kotlin or Swift. Local database plus a mocked sync API |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Emulator or device. No paid infrastructure |
| Which | Recommended first assignment of the Mobile track |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Platform | React Native, Flutter, Kotlin or Swift. State your choice and why | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/react/react-original.svg" alt="React Native" title="React Native" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/flutter/flutter-original.svg" alt="Flutter" title="Flutter" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/kotlin/kotlin-original.svg" alt="Kotlin" title="Kotlin" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/swift/swift-original.svg" alt="Swift" title="Swift" height="32"> |
| Storage | Local database on the device | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/sqlite/sqlite-original.svg" alt="SQLite" title="SQLite (example)" height="32"> |
| Backend | Mocked sync API | — |

## Evaluation weights

| Area | Weight |
|---|---|
| Offline persistence and data model | 20% |
| Sync queue, retry and idempotency | 25% |
| Conflict policy and restart recovery | 20% |
| Code structure and reuse (UI / logic / storage / network separated) | 15% |
| Testing and error handling | 10% |
| UX states and accessibility | 10% |

Visual polish is secondary to correct, explainable sync behaviour.

## Read next

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../mobile-instructions.md](../mobile-instructions.md) (mandatory for every assignment)
- [../README.md](../README.md)
