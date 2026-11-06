# Assignment 02 — Design System Notes

**v1.0 — 2026-11-06** · Extends [../../../shared/design-system/README.md](../../../shared/design-system/README.md)

| Area | Guidance |
|---|---|
| Editor | Keyboard first: Enter new bullet, Tab indent, Shift+Tab outdent, Alt+Up/Down reorder |
| Bullets | Visible bullet handle, collapse chevron, indent guides |
| Node types | Small type chip or icon per node (task, meeting, idea, decision, link). Not colour alone |
| Tasks | Checkbox; done state with strike-through and text |
| Date navigation | Previous, next, today, date picker |
| Status bar | Online/offline badge and sync state: synced, pending (count), syncing, error |
| AI panel | Side panel. Original text on one side, suggestions on the other |
| AI review | Each suggestion is editable and has Accept and Dismiss. "Apply selected" is explicit |
| AI failure | Inline message with Retry. Notes remain usable |
| Search | Single box with filters: date range, node type, tags |
| Empty day | Friendly empty state with one clear first action |

## Component additions

| Component | States |
|---|---|
| Node row | default, focused, selected, collapsed, dragging |
| Sync badge | synced, pending, syncing, offline, error |
| Suggestion card | proposed, edited, accepted, dismissed |
| Type chip | text, task, meeting, idea, decision, link |

## Wording
- AI suggestions are labelled "Suggested by AI. Review before applying."
- Offline banner: "You're offline. Changes are saved on this device and will sync later."

## Samples
See [../samples/](../samples/).
