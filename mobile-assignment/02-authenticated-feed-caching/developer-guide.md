# Assignment 02 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on sound session and data-flow engineering, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order (about 7 h)

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Mock API: sign in, short-lived access token, refresh token, paged feed. Switches for token lifetime, latency, 401 and 5xx | You can force expiry and failure from config | 1 h |
| 2 | One API client, secure token storage, sign in and sign out | Tokens sit in Keychain / Keystore. Sign out clears tokens and cache | 1.5 h |
| 3 | Refresh: one shared in-flight refresh, retry the original call | Ten parallel 401s cause one refresh. Invalid refresh token gives clean sign-out | 1.5 h |
| 4 | Paginated feed with infinite scroll and pull to refresh | No duplicate page requests. Page 3 error keeps pages 1–2 with inline retry | 1 h |
| 5 | Feed cache with timestamp and staleness rule | Reopen shows cached feed instantly, then updates. Offline shows cache with indicator | 1 h |
| 6 | States and accessibility: loading, empty, error with retry, offline | Every state reachable. Screen reader labels and large text work | 0.5 h |
| 7 | Tests, README, demo video | Checklist C is complete | 0.5 h |

Session and refresh logic first. UI polish comes last.

## 2. Directions

| Topic | Direction |
|---|---|
| Token storage | Platform secure storage (Keychain / Keystore). Never plain preferences, files or logs |
| One client | All API calls go through one client that handles 401 and refresh. No refresh logic in screens |
| Refresh race | Share one in-flight refresh across concurrent calls, then retry each original request |
| Expired session | Refresh fails: clear tokens, return to sign-in with a clear message, keep the user's place if safe |
| Cache | Show cached data first, then revalidate. Store a timestamp and state the staleness rule |
| Sign out | Clear tokens and cached user data |
| States | Handle loading, empty, error with retry and offline with cached data explicitly |
| Pagination | Cursor or page based. Guard against duplicate page requests |
| Structure | Keep UI, logic, storage and networking separate. No HTTP or storage calls in UI components |
| Secrets | No fixed credentials or secrets in the bundle. Synthetic users and content only |
| Live change | Keep the code ready to cut access token lifetime to 10 seconds, or add a "like" with optimistic update and rollback |
| Scope | Record assumptions and known gaps in the README. Mark AI-assisted code |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../mobile-instructions.md](../mobile-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 02 (the one selected for you)
- [ ] Choose React Native, Flutter, Kotlin or Swift. Note why
- [ ] Verify the toolchain and an emulator (or device) run a hello-world locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets)
- [ ] Choose the secure storage API for your platform
- [ ] Sketch the session lifecycle: sign in, expiry, refresh, revoked, sign out
- [ ] Choose cursor or page pagination and the cache staleness rule
- [ ] Decide the 5 or more tests (refresh, concurrent 401s, pagination, cache, one error case)
- [ ] Plan the 7 steps above against your available hours

## 4. Checklist B — While developing

### Session and security
- [ ] Tokens stored only in secure storage. Search code and logs for token leaks
- [ ] Input validated on sign in, errors shown
- [ ] Single in-flight refresh shared by concurrent requests (test with parallel 401s)
- [ ] Access token expires mid-scroll: one silent refresh, request retried, user unaware
- [ ] Refresh token invalid or revoked: clean sign-out with a clear message
- [ ] Sign out clears tokens and cached user data
- [ ] You know what is deliberately not stored
- [ ] No secrets or fixed credentials in the bundle

### Feed and cache
- [ ] Infinite scroll with no duplicate page requests
- [ ] Pull to refresh works
- [ ] Reopen after kill: still signed in, cached feed shown immediately, then updated
- [ ] Offline: cached feed with an offline indicator, refresh fails gracefully
- [ ] Server error on page 3: pages 1–2 stay visible, inline retry
- [ ] Empty feed shows a helpful empty state, not a blank screen
- [ ] Slow network: skeleton or spinner, timeouts

### Mobile
- [ ] Airplane-mode test done on an emulator or device
- [ ] Layout works on at least two screen sizes and at large text
- [ ] Screen reader labels present in the feed

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record AI tool usage as you go. You must be able to explain it

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, start mock API, run app, test. All work
- [ ] At least 5 meaningful tests pass: refresh, concurrent 401s, pagination, cache, one error case
- [ ] Rehearse the scenarios: offline, app killed, slow network, expiry mid-scroll, revoked refresh token, empty feed, page 3 error
- [ ] Live-change rehearsal: set access token lifetime to 10 seconds and stay signed in. Try a "like" with rollback on failure

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits
- [ ] Demo video on emulator or device: sign in, scroll, offline, kill and reopen, token expiry
- [ ] Mocked API runs locally with expiry and failure switches
- [ ] README: stack choice and why, storage decisions, trade-offs, known gaps
- [ ] README answers the depth checks: where tokens live, parallel refresh, cache clearing on sign out, screen reader and text scaling
- [ ] AI usage disclosed

### Hygiene
- [ ] No secrets or real data in git history
- [ ] No dead code, stray debug logs or hidden TODOs
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk through the session lifecycle and where each piece of data lives
- [ ] Can explain the refresh race and how you handled it
- [ ] Can explain the cache staleness rule and how you tested expiry
- [ ] Can identify and explain AI-generated code
- [ ] Ready for the live change from section E

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Tokens in plain preferences or logs | Keychain / Keystore only |
| Refresh logic in several screens | One API client |
| Ten 401s trigger ten refreshes | One shared in-flight refresh |
| Cache left after sign out | Clear tokens and cache together |
| Blank screen while loading | Show cached data first, then revalidate |
| Only the happy path | Loading, empty, error and offline states |
| Page error wipes the list | Keep loaded pages, inline retry |
| Fixed credentials in the bundle | Mock sign-in with synthetic users |
| Polished UI, thin session tests | Refresh and expiry first |
