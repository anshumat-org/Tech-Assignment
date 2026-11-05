# Assignment 02 — Samples

**v1.0 — 2026-11-06** · Look-and-feel references only. They are **not** solutions.

| File | Type | Shows |
|---|---|---|
| [daily-outliner.svg](daily-outliner.svg) | Wireframe | Date navigation, nested bullets, type chips, status bar |
| [ai-review-panel.svg](ai-review-panel.svg) | Wireframe | Original vs editable AI suggestions, apply and dismiss |
| [sync-status-states.svg](sync-status-states.svg) | Wireframe | Five sync states with text labels |
| [prototype.html](prototype.html) | Clickable prototype | Enter, Tab, Shift+Tab, Backspace; node types; offline toggle; mock AI review |

**Open the prototype:** open `prototype.html` in a browser from this folder.

**Prototype limits (by design)**
- In-memory only. It loses data on refresh. No IndexedDB, sync queue, backend or conflict handling.
- The AI is a fixed mock. A real build needs a provider interface, schema validation, timeouts and server-side keys.
- No drag reorder, Markdown, search or tags. Your submission must implement these.
