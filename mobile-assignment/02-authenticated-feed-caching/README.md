# Assignment 02 — Authenticated Feed with Caching

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | A sign-in flow and a paginated feed with caching, against a mocked authenticated API |
| Why | Tests secure token handling, session lifecycle and graceful behaviour on bad networks |
| Who | A signed-in user who scrolls a feed, refreshes it and returns to the app later |
| How | React Native, Flutter, Kotlin or Swift. Mocked API issuing short-lived tokens |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Emulator or device. No paid infrastructure |
| Which | Second assignment of the Mobile track, after 01 |

## Evaluation weights

| Area | Weight |
|---|---|
| Secure token storage and session handling | 25% |
| Token refresh and expired-session flow | 20% |
| Pagination, caching and pull to refresh | 20% |
| Code structure and reuse (UI / logic / storage / network separated) | 15% |
| Testing and error handling | 10% |
| UX states and accessibility (loading, empty, error) | 10% |

Visual polish is secondary to sound session and data-flow engineering.

## Read next

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../mobile-instructions.md](../mobile-instructions.md) (mandatory for every assignment)
- [../README.md](../README.md)
