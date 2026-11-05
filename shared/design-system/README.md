# Shared Design System

**v1.0 — 2026-11-06**

Starting point for both assessments. Tokens live in [tokens.css](tokens.css). Candidates may extend or replace them, but must document the result in their own `docs/design-system.md` (format: [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md), Section 5).

| Part | Guidance |
|---|---|
| Principles | Clear, low friction, accessible, calm |
| Colour | Navy text, teal primary, light surface. Light and dark themes both required |
| Type | One sans family, mono for code and SQL. Scale: 12 / 14 / 16 / 20 / 28 |
| Spacing | 4px base grid |
| Radius | 4 / 8 / 12 |
| Contrast | Body text ≥ 4.5:1. Never use colour alone to carry meaning |
| Focus | Visible 2px focus ring using `--color-focus` |
| Motion | Short, optional; respect `prefers-reduced-motion` |

## Core components

| Component | Variants | Required states |
|---|---|---|
| Button | primary, secondary, danger, ghost | default, hover, focus, disabled, loading |
| Input / Textarea | text, search | default, focus, error, disabled |
| Select / Checkbox / Radio | — | default, focus, checked, disabled |
| Card | plain, selectable | default, selected, hover |
| Table | dense, comfortable | empty, loading, error |
| Badge / Status chip | neutral, success, warning, danger | — |
| Dialog | confirm, destructive | focus trap, Esc to close |
| Toast / Banner | info, success, error, offline | dismissible, announced to screen readers |
| Progress / Timer | linear, countdown | warning threshold |

## Rules

- ⭐ Define tokens once. No hard-coded colours or sizes in components.
- ⭐ Every interactive element works by keyboard.
- ⚠️ Destructive actions need a deliberate confirmation step.
- ⚠️ Every list or page needs loading, empty and error states.
