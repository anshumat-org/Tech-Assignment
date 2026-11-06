# Assignment 02 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Functional requirements
- Sign in with email and password against the mock API. Validate input and show errors.
- Mock API returns a short-lived access token and a longer-lived refresh token.
- Paginated feed (cursor or page based) with infinite scroll.
- Pull to refresh. Cached feed shown instantly on next launch, then updated.
- Sign out clears tokens and cached user data.
- Distinct states: loading, empty, error with retry, offline with cached data.

### B. Session and storage (suggested)

| Part | Suggested design |
|---|---|
| Tokens | Keychain / Keystore or platform secure storage. Never plain preferences or logs |
| Refresh | Single in-flight refresh shared by concurrent requests, then retry the original call |
| Expired session | Refresh fails: clear tokens, return to sign-in, keep the user's place if safe |
| Feed cache | Local database or file cache with a timestamp and a staleness rule |
| Mock API | Configurable token lifetime, latency, 401 and 5xx injection |

### C. Scenarios to address

| Scenario | Expected behaviour |
|---|---|
| Offline | Cached feed shown with an offline indicator; refresh fails gracefully |
| App killed | Reopen stays signed in and shows cached feed immediately |
| Slow network | Skeleton or spinner, timeouts, no duplicate page requests |
| Access token expires mid-scroll | One silent refresh, request retried, user unaware |
| Refresh token invalid or revoked | Clean sign-out with a clear message |
| Empty feed | Helpful empty state, not a blank screen |
| Server error on page 3 | Pages 1–2 stay visible, inline retry |

### D. Engineering depth checks (answer in README)
- Where are tokens stored, and what is deliberately not stored?
- What stops ten parallel requests from triggering ten refreshes?
- How is cached data cleared on sign out, and why does it matter?
- How are screen reader labels and text scaling handled in the feed?

### E. Live follow-up
The interviewer may ask you to shorten the access token lifetime to 10 seconds and show the app staying signed in, or to add a "like" action with optimistic update and rollback on failure. Structure the code so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Store tokens in platform secure storage | Put tokens in plain preferences, files or logs |
| Funnel all API calls through one client that handles 401 and refresh | Scatter refresh logic across screens |
| Share one in-flight refresh across concurrent calls | Fire parallel refreshes |
| Show cached data first, then revalidate | Show a blank screen while loading |
| Handle loading, empty, error and offline states explicitly | Show only the happy path |
| Clear tokens and cache on sign out | Leave user data behind |
| Keep UI, logic, storage and networking separate | Call HTTP or storage from UI components |
| Record assumptions and mark AI-assisted code | Ship secrets or fixed credentials in the bundle |

### Deliverables

| Item | Format reference |
|---|---|
| Git repo with setup instructions and meaningful commits | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7 |
| Demo video on emulator or device: sign in, scroll, offline, kill and reopen, token expiry | Section 8 |
| Mocked API, runnable locally, with expiry and failure switches | Section 7 |
| At least five meaningful tests (refresh, concurrent 401s, pagination, cache, one error case) | Section 6 |
| Short README: stack choice and why, storage decisions, trade-offs, known gaps | Section 7 |

### Constraints
- React Native, Flutter, Kotlin or Swift. State the choice and why.
- Mocked backend only. Synthetic users and content only.
- Follow [../mobile-instructions.md](../mobile-instructions.md).
- Works on at least two screen sizes and supports large text.

### Technical discussion (30–45 min)
Walk through the session lifecycle, where each piece of data lives, the refresh race and how you handled it, the cache staleness rule, and how you tested expiry. Identify AI-generated code and explain it. Expect a live change from section E.
