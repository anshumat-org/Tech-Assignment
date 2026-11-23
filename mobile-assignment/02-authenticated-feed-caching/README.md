# Assignment 02 — Authenticated Feed with Caching

**v0.3 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | A sign-in flow and a paginated feed with caching, against a mocked authenticated API |
| Why | Tests secure token handling, session lifecycle and graceful behaviour on bad networks |
| Who | A signed-in user who scrolls a feed, refreshes it and returns to the app later |
| How | React Native, Flutter, Kotlin or Swift. Mocked API issuing short-lived tokens |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Emulator or device. No paid infrastructure |
| Which | Second assignment of the Mobile track, after 01 |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Platform | React Native, Flutter, Kotlin or Swift. State your choice and why | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/react/react-original.svg" alt="React Native" title="React Native" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/flutter/flutter-original.svg" alt="Flutter" title="Flutter" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/kotlin/kotlin-original.svg" alt="Kotlin" title="Kotlin" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/swift/swift-original.svg" alt="Swift" title="Swift" height="32"> |
| Storage | Device cache. Secure token storage | — |
| Backend | Mocked API issuing short-lived tokens | — |

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

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../mobile-instructions.md](../mobile-instructions.md) (mandatory for every assignment)
- [../README.md](../README.md)
