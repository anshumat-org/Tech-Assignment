# Assignment 01 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Components (build 6–8)

| Component | Required behaviour |
|---|---|
| Button | primary, secondary, danger, ghost. default, hover, focus, disabled, loading |
| Input | Label, hint, error text linked by `aria-describedby`. Error and disabled states |
| Select | Native or custom. If custom, full listbox keyboard pattern |
| Modal dialog | Focus trap, Esc closes, focus returns to trigger, scroll lock |
| Tabs | Arrow keys, Home / End, roving tabindex, correct roles |
| Toast | Announced via live region, dismissible, auto-dismiss that can be paused |
| Checkbox or Radio group | Group label, checked and disabled states |
| Tooltip or Badge (optional) | Not colour-only, reachable by keyboard |

### B. Design tokens
- Colour, spacing, radius, type and focus ring defined once (CSS variables or equivalent).
- Light and dark themes both work by swapping tokens only.
- No hard-coded colours or sizes inside components.

### C. Accessibility baseline
- Every interactive element works by keyboard with a visible focus ring.
- Contrast: body text at least 4.5:1. Meaning never carried by colour alone.
- Respect `prefers-reduced-motion`.
- Usable at 320 px width and at 200% zoom.

### D. Scenarios to address (answer in README)
- A user opens a modal, tabs through it and presses Esc. Where does focus go?
- A toast appears while a screen reader user is typing in an input. What is announced, and when?
- Two tab panels have very different heights. How do you avoid layout jump?
- A consumer needs a Button that renders as a link. How does your API allow it?
- How do you prevent double submit on a loading Button?

### E. Demo and tests
- Demo page (or Storybook) showing every component in every state, plus a theme toggle.
- Tests for behaviour, not snapshots only: keyboard interaction, ARIA attributes, focus management.
- At least one automated accessibility check (for example axe) on the demo or components.

### F. Live follow-up
The interviewer may ask you to add a **Combobox with async suggestions** or a **destructive confirm variant** of the modal. Reuse existing parts so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Use semantic HTML first, ARIA only to fill gaps | Add ARIA roles that duplicate native semantics |
| Read all colours, spacing and radii from tokens | Hard-code hex values or pixel sizes in components |
| Keep a small, consistent props API (variant, size, disabled) | Add a prop for every one-off need |
| Forward refs and native attributes | Wrap elements so consumers cannot reach them |
| Test keyboard and focus behaviour | Rely on visual checks only |
| Document trade-offs, such as native vs custom select | Pull in a large UI kit to do the work for you |
| Mark AI-generated or reused code and verify it | Submit code you cannot explain |

### Deliverables

| Item | Format reference |
|---|---|
| Git repo with setup instructions and meaningful commits | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7 |
| Demo page or Storybook, plus short video or screenshots | Section 8 |
| Design system notes (`docs/design-system.md`) | Section 5 |
| At least eight meaningful tests, including keyboard and focus | Section 6 |
| Short README with assumptions and trade-offs | Section 7 |

### Constraints
- Any framework. TypeScript preferred.
- No mock API needed. If you add sample data, keep it synthetic.
- Headless libraries are allowed only if you can explain what they do for you.
- Follow [../frontend-instructions.md](../frontend-instructions.md).

### Technical discussion (about 30 min)
Walk through one component's keyboard model, your token structure, one accessibility bug you found and fixed, and which files change to add a new variant. Expect a small live change.
