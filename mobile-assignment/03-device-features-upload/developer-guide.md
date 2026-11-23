# Assignment 03 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on correct permission and upload behaviour, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order (about 7 h)

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Permission wrapper: granted / denied / permanently denied / limited | Each state is unit tested and has a UI outcome | 1 h |
| 2 | Report form: title, note, camera or gallery photo, one-shot location | Photo is copied to app storage. Location off or denied still lets you save | 1.5 h |
| 3 | Photo compress or resize, and low-storage or large-photo errors | Upload size drops. Errors show a message, no crash | 0.5 h |
| 4 | Mock upload endpoint with latency, mid-upload drops, 5xx and 413 | You can trigger each failure from config | 1 h |
| 5 | Persisted upload queue, idempotency key per report, backoff with cap | Retry creates no duplicate. Queue survives app kill | 1.5 h |
| 6 | Progress, cancel, report list states, background upload via platform API | Queued / Uploading / Done / Failed shown with real progress. Resumes after backgrounding | 1 h |
| 7 | Tests, README, demo video | Checklist C is complete | 0.5 h |

Permissions and the upload queue first. UI polish comes last.

## 2. Directions

| Topic | Direction |
|---|---|
| Permissions | Ask camera and location only at the moment of use, with a short rationale. Request the minimum |
| States | Handle denied, permanently denied, limited and revoked. Never assume granted |
| Alternatives | Denied: offer gallery pick or manual place entry. Permanently denied: explain and link to system settings, no repeated prompts |
| Location | Coarse unless precise is justified. One-shot fix with a timeout. Services off: save without location |
| Media | Copy captured file to app storage, not a temp path that may vanish. Compress or resize before upload |
| Upload queue | Persisted queue, resumable or chunked if feasible, idempotency key per report |
| Retry | Automatic with backoff and cap, plus manual retry. No unbounded loops |
| Background | Use the platform background API (WorkManager, BGTaskScheduler or equivalent) |
| Structure | Keep UI, logic, storage and networking separate. No platform or HTTP calls in UI components |
| Data | Synthetic content only. No real personal photos. Know what location and photo data is kept and whether EXIF is stripped |
| Live change | Keep the code ready for multiple photos per report with per-file progress, or permission revoked while the app is open |
| Scope | Record assumptions and known gaps in the README. Mark AI-assisted code |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../mobile-instructions.md](../mobile-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 03 (the one selected for you)
- [ ] Choose React Native, Flutter, Kotlin or Swift. Note why
- [ ] Verify the toolchain runs. A real device is better for camera. Know how to fake camera and location on the emulator
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets)
- [ ] List the permissions you need and justify each as the minimum
- [ ] Sketch the upload queue lifecycle: Queued, Uploading, Done, Failed
- [ ] Choose the background mechanism for your platform
- [ ] Decide the 5 or more tests (permission states, retry, idempotency, queue restore, one error case)
- [ ] Plan the 7 steps above against your available hours

## 4. Checklist B — While developing

### Permissions
- [ ] Permission asked only at the moment of use, with a rationale
- [ ] Denied: effect explained, alternative offered (gallery pick, manual place)
- [ ] Permanently denied: explained, link to system settings, no repeated prompts
- [ ] Limited and revoked-while-open states handled
- [ ] No permission or library added that you do not need

### Media and location
- [ ] Captured file copied to app storage
- [ ] Photo compressed or resized before upload
- [ ] Location is a one-shot fix with a timeout. Location services off still allows saving
- [ ] Low storage or very large photo: graceful error, no crash
- [ ] You know what photo and location data is kept, for how long, and whether EXIF is stripped

### Upload
- [ ] Queue is persisted. Kill mid-upload: it resumes or restarts once, no duplicate report
- [ ] Idempotency key per report. Retry does not duplicate (test it)
- [ ] Backoff with cap. Manual retry available
- [ ] Real progress per report, with a cancel option and a timeout
- [ ] Offline: report saved, uploads on reconnect
- [ ] Mock 5xx, 413 and mid-upload drop each give a clear state
- [ ] Background API used, not a hand-rolled loop

### Mobile
- [ ] Airplane-mode test done on an emulator or device
- [ ] Layout works on at least two screen sizes and at large text. Screen reader labels present

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record AI tool usage as you go. You must be able to explain it

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, start mock endpoint, run app, test. All work
- [ ] At least 5 meaningful tests pass: permission states, retry, idempotency, queue restore, one error case
- [ ] Rehearse the scenarios: denied, permanently denied, location off, offline, kill mid-upload, slow network, low storage or large photo
- [ ] Live-change rehearsal: revoke a permission in system settings while the app is open and show recovery. Try multiple photos with per-file progress

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits
- [ ] Demo video on emulator or device: grant, deny, permanent deny, offline, kill mid-upload
- [ ] Mocked upload endpoint runs locally with failure switches
- [ ] README: stack choice and why, permissions list, trade-offs, known gaps
- [ ] README answers the depth checks: permissions and why minimum, data kept and EXIF, duplicate prevention, small screen and screen reader
- [ ] AI usage disclosed

### Hygiene
- [ ] No secrets or real data in git history. No real personal photos in the repo
- [ ] No dead code, stray debug logs or hidden TODOs
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk through each permission state
- [ ] Can explain the upload queue lifecycle and duplicate prevention
- [ ] Can explain background behaviour per platform and what data is stored
- [ ] Can identify and explain AI-generated code
- [ ] Ready for the live change from section E

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Asking for all permissions on first launch | Ask in context, with a rationale |
| Assuming permission is granted | Handle every state, including revoked |
| Dead end after denial | Offer gallery pick or manual place |
| Repeated prompts after permanent denial | Explain and link to settings |
| Photo kept at a temp path | Copy to app storage |
| Upload state only in memory | Persist the queue and test kill mid-upload |
| Blind re-upload on retry | Idempotency key per report |
| Unbounded retry loop | Backoff, cap and platform background API |
| Crash on large photo or low storage | Compress, and show a graceful error |
| Polished UI, thin permission and upload tests | Permissions and queue first |
