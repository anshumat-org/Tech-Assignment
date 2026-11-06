# Assignment 01 — Design System Notes

**v1.0 — 2026-11-06** · Extends [../../../shared/design-system/README.md](../../../shared/design-system/README.md)

| Area | Guidance |
|---|---|
| Candidate screens | Calm, distraction-free, high contrast. One question focus at a time |
| Timer | Always visible. Warning colour plus text at 5 minutes left. Never colour alone |
| Question navigator | Numbered chips with states: unanswered, answered, flagged, current |
| Option controls | Radio for single, checkbox for multiple, 5-point scale for Likert. Large hit areas |
| Save feedback | "Saved" indicator after each answer; visible failure state if save fails |
| Submit | Review screen, then a confirm dialog stating unanswered count |
| Admin screens | Dense tables with filters (category, difficulty, status). Archive needs confirmation |
| Blueprint editor | Quota table with a live "available vs required" count per row; red when short |
| Results | Section totals as table. Psychometric dimensions as bars with an **Illustrative only** label |

## Component additions

| Component | States |
|---|---|
| Question card | default, answered, flagged |
| Timer | normal, warning, expired |
| Quota row | enough, short, error |
| Dimension bar | with value and label; no good/bad colouring |

## Wording
- Psychometric results: "Illustrative summary. Not a clinical or diagnostic result."
- Never describe personality answers as right or wrong.

## Samples
See [../samples/](../samples/).
