# Assignment 03 — Device Features and Upload

**v0.3 DRAFT — 2026-11-23**

| WH | Answer |
|---|---|
| What | An app that captures or picks a photo, tags it with location, and uploads it reliably to a mocked backend |
| Why | Tests permission handling, platform APIs and uploads that survive interruptions |
| Who | A field user who attaches photos and locations to reports on an unreliable connection |
| How | React Native, Flutter, Kotlin or Swift. Mocked upload endpoint with progress and failures |
| When | 6–8 hours of effort. Review 30–45 minutes |
| Where | Emulator or device (a real device is better for camera). No paid infrastructure |
| Which | Third assignment of the Mobile track, after 01 and 02 |

## Tech stack

| Layer | Stack | Logos |
|---|---|---|
| Platform | React Native, Flutter, Kotlin or Swift. State your choice and why | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/react/react-original.svg" alt="React Native" title="React Native" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/flutter/flutter-original.svg" alt="Flutter" title="Flutter" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/kotlin/kotlin-original.svg" alt="Kotlin" title="Kotlin" height="32"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@v2.16.0/icons/swift/swift-original.svg" alt="Swift" title="Swift" height="32"> |
| Storage | Persisted upload queue on the device | — |
| Backend | Mocked upload endpoint with progress and failures. No real personal photos | — |

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

- [product-brief.md](product-brief.md) (start here: product, personas, capabilities, user stories with acceptance criteria)
- [requirements-and-directives.md](requirements-and-directives.md)
- [resources.md](resources.md)
- [developer-guide.md](developer-guide.md) (build order, directions, before / during / after checklists)
- [../mobile-instructions.md](../mobile-instructions.md) (mandatory for every assignment)
- [../README.md](../README.md)
