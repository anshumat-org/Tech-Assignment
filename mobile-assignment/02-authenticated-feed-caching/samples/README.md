# Assignment 02 — Authenticated Feed with Caching — Samples

**v0.1 DRAFT — 2026-11-23** · Look-and-feel references only. They are **not** solutions.

One wireframe per screen in [product-brief.md](../product-brief.md) section 6. A second file appears only where a non-default state is central to the assignment.

| File | Screen | Shows |
|---|---|---|
| [S-01-launch-session-check.svg](screens/S-01-launch-session-check.svg) | S-01 Launch / session check | Splash while tokens are checked, routing note |
| [S-02-sign-in.svg](screens/S-02-sign-in.svg) | S-02 Sign in | Email, password, inline validation error, session-expired message |
| [S-03-feed.svg](screens/S-03-feed.svg) | S-03 Feed | Cached items while revalidating, next-page loader, pull to refresh, Sign out |
| [S-03-feed-offline.svg](screens/S-03-feed-offline.svg) | S-03 Feed (offline with cache) | Offline banner, cached items, page error with Retry |
| [S-04-sign-out-confirm.svg](screens/S-04-sign-out-confirm.svg) | S-04 Sign out confirm | Dialog explaining local data removal, Sign out, Cancel |
| [S-05-tester-debug.svg](screens/S-05-tester-debug.svg) | S-05 Tester / debug screen | Token lifetime, latency, force 401, force 5xx, recent requests |

**Limits (by design)**
- Static SVG wireframes. Names, text and numbers are placeholders.
- System dialogs and pickers are generic sketches; real wording and options come from the OS.
- Your layout, wording and styling may differ. Every status must carry a text label or icon, not colour alone.
