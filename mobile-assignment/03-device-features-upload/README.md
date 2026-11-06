# Assignment 03 — Device Features and Upload

**v0.1 DRAFT — 2026-11-06**

| WH | Answer |
|---|---|
| What | An app that captures or picks a photo, tags it with location, and uploads it reliably to a mocked backend |
| Why | Tests permission handling, platform APIs and uploads that survive interruptions |
| Who | A field user who attaches photos and locations to reports on an unreliable connection |
| How | React Native, Flutter, Kotlin or Swift. Mocked upload endpoint with progress and failures |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Emulator or device (a real device is better for camera). No paid infrastructure |
| Which | Third assignment of the Mobile track, after 01 and 02 |

## Evaluation weights

| Area | Weight |
|---|---|
| Permission flows, including denial and settings redirect | 25% |
| Upload reliability: retry, progress, background safety | 25% |
| Camera / photo pick and location handling | 15% |
| Code structure and reuse (UI / logic / storage / network separated) | 15% |
| Testing and error handling | 10% |
| UX states and accessibility | 10% |

Visual polish is secondary to correct permission and upload behaviour.

## Read next

- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [../mobile-instructions.md](../mobile-instructions.md) (mandatory for every assignment)
- [../README.md](../README.md)
