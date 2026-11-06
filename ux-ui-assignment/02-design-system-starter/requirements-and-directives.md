# Assignment 02 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Foundations and tokens
- Colour, type scale, spacing (4px grid suggested), radius, elevation, motion.
- Two layers: raw values and semantic tokens (e.g. text-primary, surface, border-focus).
- Light and dark values for every semantic colour.
- Document naming rules and how to add a token.

### B. Components (8–10)
Choose from the list below or justify alternatives.

| Component | Required states |
|---|---|
| Button | default, hover, focus, active, disabled, loading |
| Text input | default, focus, filled, error, disabled |
| Select or combobox | closed, open, focus, error, disabled |
| Checkbox and radio | unchecked, checked, focus, disabled, error |
| Badge or status chip | neutral, success, warning, danger |
| Card | default, hover, selected |
| Table or list row | default, selected, empty, loading |
| Dialog | confirm, destructive, focus trap, Esc to close |
| Toast or banner | info, success, error, announced |
| Tabs or navigation item | default, current, focus, disabled |

### C. Accessibility rules
- Contrast targets and a verification table for all text and UI tokens, both themes.
- Focus ring spec, keyboard behaviour per component, target size.
- Text alternatives, labels, error association, no colour-only meaning.
- Respect reduced motion.

### D. Usage guidance
- For each component: when to use, when not to, content rules, do and don't examples.
- One composed example screen (a form with a table or dialog) using only the system.

### E. Scenarios to address
- A button label doubles in length in another language. What breaks?
- A brand colour fails contrast in dark mode. How do you fix it without touching components?
- A team asks for a one-off card variant. What is your decision process?

### F. Live follow-up
The interviewer may ask you to add a **warning** variant to one component, or a new semantic token, and update documentation and both themes live without creating inconsistency.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Define tokens once, reference them everywhere | Hard-code colours or sizes inside components |
| Use semantic names that survive theming | Name tokens by hue only (e.g. blue-500 in components) |
| Show every required state per component | Show only default and hover |
| Verify contrast in both themes | Assume dark mode passes because light passes |
| Write when-not-to-use guidance | Document only the happy path |
| Disclose AI-generated assets and copy, and review them | Submit unreviewed AI output |
| Keep the set small and complete | Build many half-finished components |

### Deliverables

| Item | Format |
|---|---|
| Design file | Candidate's choice: Figma link (view access) or exported PDF/PNG set |
| Token table or file | CSS, JSON, or table in the file or rationale doc |
| Component sheets with states, light and dark | Inside the file or exports |
| Accessibility verification table | Rationale doc |
| Usage guidance and composed example screen | Inside the file or exports |
| Rationale doc (1–2 pages) | Markdown or PDF: decisions, trade-offs, assumptions, AI use |

### Constraints
- Starting point may be [../../shared/design-system/README.md](../../shared/design-system/README.md). Extend or replace, and explain.
- Freely licensed fonts and icons only.
- Synthetic content only. No real brands.
- 8–10 components. Light and dark both required.

### Design discussion (30–45 min)
Walk through the token layers, one component and all its states, one contrast fix, one decision you rejected, which assets were AI-assisted and how you verified them, and the live variant change.
