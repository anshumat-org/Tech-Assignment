# Assignment 03 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Functional requirements
- Create a report: title, note, one photo (camera or gallery pick) and current location.
- Ask for camera and location permissions only at the moment of use, with a short rationale.
- Show upload progress per report and a list of reports with states (Queued / Uploading / Done / Failed).
- Retry failed uploads automatically with backoff, and manually on demand.
- Uploads continue or resume safely when the app is backgrounded or killed.
- Compress or resize the photo before upload.

### B. Design pointers (suggested)

| Part | Suggested design |
|---|---|
| Permissions | One wrapper that returns granted / denied / permanently denied / limited |
| Media | Store captured file in app storage, not a temporary path that may vanish |
| Location | Coarse unless precise is justified. One-shot fix with a timeout |
| Upload queue | Persisted queue, resumable or chunked if feasible, idempotency key per report |
| Background | Platform background task API (WorkManager, BGTaskScheduler or equivalent) |
| Mock API | Configurable latency, drops mid-upload, 5xx and 413 responses |

### C. Scenarios to address

| Scenario | Expected behaviour |
|---|---|
| Permission denied | Explain the effect, offer an alternative (pick from gallery, enter place by hand) |
| Permanently denied | Explain and link to system settings, no repeated prompts |
| Location services off | Clear message, report can still be saved without location |
| Offline | Report saved and queued, uploads on reconnect |
| App killed mid-upload | Upload resumes or restarts once, no duplicate report |
| Slow network | Real progress, cancel option, timeout and retry |
| Low storage or large photo | Graceful error, no crash |

### D. Engineering depth checks (answer in README)
- Which permissions are requested, when, and why are they the minimum?
- What location and photo data is kept, for how long, and is any EXIF data stripped?
- How do you prevent duplicate uploads on retry?
- How does it behave on small screens and with a screen reader?

### E. Live follow-up
The interviewer may ask you to allow multiple photos per report with per-file progress, or to revoke the permission in system settings while the app is open and show the app recovering. Structure the code so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Request permissions in context, with a rationale | Ask for everything on first launch |
| Handle denied, permanently denied, limited and revoked states | Assume permission is granted |
| Offer an alternative path when a permission is refused | Dead-end the user |
| Persist the upload queue and copy media to app storage | Keep upload state only in memory |
| Use an idempotency key so retries cannot duplicate | Re-upload blindly |
| Use platform background APIs and cap retries with backoff | Run unbounded loops that drain battery |
| Keep UI, logic, storage and networking separate | Call platform or HTTP APIs from UI components |
| Record assumptions and mark AI-assisted code | Add unneeded permissions or libraries |

### Deliverables

| Item | Format reference |
|---|---|
| Git repo with setup instructions and meaningful commits | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7 |
| Demo video on emulator or device: grant, deny, permanent deny, offline, kill mid-upload | Section 8 |
| Mocked upload endpoint, runnable locally, with failure switches | Section 7 |
| At least five meaningful tests (permission states, retry, idempotency, queue restore, one error case) | Section 6 |
| Short README: stack choice and why, permissions list, trade-offs, known gaps | Section 7 |

### Constraints
- React Native, Flutter, Kotlin or Swift. State the choice and why.
- Mocked backend only. Synthetic content only; do not upload real personal photos.
- Follow [../mobile-instructions.md](../mobile-instructions.md).
- Works on at least two screen sizes and supports large text.

### Technical discussion (30–45 min)
Walk through each permission state, the upload queue lifecycle, background behaviour per platform, duplicate prevention, and what data is stored. Identify AI-generated code and explain it. Expect a live change from section E.
