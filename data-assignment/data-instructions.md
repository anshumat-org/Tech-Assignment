# Data Instructions

**v0.1 DRAFT — 2026-11-06** · Mandatory engineering principles for all Data assignments. Assignments for this track are not yet defined.

| # | Principle | Rule |
|---|---|---|
| 1 | Human-defined data work | Questions, metric definitions, business rules and assumptions come from humans. Understand the data and the question first. AI assistants may be used but must not invent metric definitions, data, rules or conclusions. Record assumptions and data limits. Clarify ambiguity instead of guessing |
| 2 | Human-approved changes | A human reviews and approves queries, transformations, schema and pipeline changes, metric definitions, model outputs and anything touching personal data. Check results against known figures. The analyst or engineer is accountable for correctness, privacy and interpretation. Run data-quality checks and explain material changes |
| 3 | Reproducible, governed, reusable | Follow existing conventions and reuse existing models, queries and utilities. Keep work in version control and make results reproducible from raw inputs. Add data-quality tests. Collect and keep only the data required. Use synthetic data only. Avoid duplicated logic, one-off scripts and silent changes to definitions |

## What you should be able to demonstrate

- Explain what you built, why, and which question or requirement drove it.
- Identify AI-generated or reused queries and code, and explain, verify and take responsibility for them.
- Reproduce a result from raw inputs, and reconcile it against a known figure.
- Show data-quality checks and what happens when one fails.
- Show where shared models or logic are reused instead of duplicated.
- State a metric definition, its denominator and its known limits.
- Make a small change without altering unrelated numbers.

**Core principle:** AI can assist the analysis. Humans own the definitions, approval and conclusions.
