# Assignment 01 — Offline-First Notes App

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | A notes (or tasks) app that works fully offline, queues changes and syncs them to a mocked backend |
| Why | Tests resilience thinking: local persistence, retries, conflicts and recovery after the app is killed |
| Who | A user who writes notes on a train, in a lift or on a weak connection |
| How | React Native, Flutter, Kotlin or Swift. Local database plus a mocked sync API |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Emulator or device. No paid infrastructure |
| Which | Recommended first assignment of the Mobile track |

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

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../mobile-instructions.md](../mobile-instructions.md) (mandatory for every assignment)
- [../README.md](../README.md)
