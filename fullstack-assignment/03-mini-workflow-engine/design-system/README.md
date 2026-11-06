# Assignment 03 — Design System Notes

**v1.0 — 2026-11-06** · Extends [../../../shared/design-system/README.md](../../../shared/design-system/README.md)

| Area | Guidance |
|---|---|
| Task list | Table or card list. Status and priority shown as chips with text, not colour alone |
| Filters | Status, priority and a search box in one row. Clear-filters action |
| Task form | One reusable form for create and edit. Inline validation messages |
| Task detail | Fields on top, chronological activity timeline below |
| Status change | One clear control (select or buttons). Show the new status immediately after success |
| States | Loading, empty, success and error are all designed |
| Delete | Confirm before delete |

## Component additions

| Component | States |
|---|---|
| Task row or card | default, hover, selected |
| Status chip | todo, in progress, done |
| Priority chip | low, medium, high |
| Activity item | created, edited, status changed, deleted |

Visual polish is secondary. Prioritise clarity and the four UI states.
