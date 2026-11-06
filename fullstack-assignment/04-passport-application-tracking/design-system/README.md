# Assignment 04 — Design System Notes

**v1.0 — 2026-11-06** · Extends [../../../shared/design-system/README.md](../../../shared/design-system/README.md)

| Area | Guidance |
|---|---|
| Simulation label | Persistent badge "Simulated. Not the official passport system" on submission and tracking views |
| Checklist | One row per requirement with a status chip: missing, pending, verified, rejected. Reason shown for rejected |
| Consent card | Plain-language purpose, scopes, retention, and a visible Withdraw action. Link to what happens after withdrawal |
| DigiLocker flow | Stepper: connect, authorise, choose documents, retrieve. Retry and a "upload instead" route on failure |
| Timeline | Vertical timeline with status, actor, time and reason. Current step highlighted |
| Operator view | Package summary, per-item accept or reject with a required reason, request-corrections action |
| Sensitive data | Mask identity numbers. Show metadata, not document contents, by default |
| Notifications | In-app list with unread state. Clear action when applicant input is required |
| States | Loading, empty, error, provider unavailable, consent withdrawn |

## Component additions

| Component | States |
|---|---|
| Checklist row | missing, pending, verified, rejected |
| Consent card | active, withdrawn, expired |
| Timeline item | past, current, future |
| Provider status banner | available, unavailable, retrying |

## Wording
- "Simulated submission. No real application has been filed."
- "You can withdraw consent at any time. Linked documents will no longer be accessible to this application."
