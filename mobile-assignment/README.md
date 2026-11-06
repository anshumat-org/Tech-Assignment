# Mobile App Assignments

**v0.1 DRAFT — 2026-11-06**

> DRAFT: content is under review and may change before use with candidates.

| # | Assignment | Focus | Effort | Review | Folder |
|---|---|---|---|---|---|
| 01 | Offline-First Notes App | Local persistence, sync queue, conflicts, restart recovery | 6–8 h | 30–45 min | [01-offline-first-notes-app](01-offline-first-notes-app/README.md) |
| 02 | Authenticated Feed with Caching | Secure tokens, refresh, expired session, paginated cache | 6–8 h | 30–45 min | [02-authenticated-feed-caching](02-authenticated-feed-caching/README.md) |
| 03 | Device Features and Upload | Camera/photo, location, permission denial, resilient upload | 6–8 h | 30–45 min | [03-device-features-upload](03-device-features-upload/README.md) |

**Recommended order:** start with 01 (resilience fundamentals), then 02 (security and sessions), then 03 (platform integration). Do not ask every applicant to complete all three. Assign one by the role's focus.

**Rules for candidates**
- Complete only the assignment selected for you.
- Read [mobile-instructions.md](mobile-instructions.md). It applies to every assignment.
- React Native, Flutter, Kotlin or Swift are all acceptable. State your choice and why.
- Backend is **mocked** (local server, in-app fake or stub). No real services or accounts.
- Use **synthetic data only**. Do not reproduce any production system.
- Submission window: 3 calendar days, then a technical discussion.
- Follow [../SUBMISSION_FORMATS.md](../SUBMISSION_FORMATS.md) and submit via the form linked in the root README.

**Each assignment folder contains**

| File | Purpose |
|---|---|
| `README.md` | Overview, WH table, evaluation weights |
| `requirements-and-directives.md` | Part 1 requirements and scenarios. Part 2 do / don't rules, deliverables, constraints, discussion |
| `resources.md` | Reference links for the topic. Starting points, not solutions |
