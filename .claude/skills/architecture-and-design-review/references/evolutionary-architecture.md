---
purpose: Meta-principle for safe architecture evolution; when to commit, defer, or reverse decisions
load-when: Evaluating architectural commitment level, assessing decision reversibility, or detecting over-design
tier: foundational
see-also:
  - solid-principles.md
  - api-contracts-and-boundaries.md
---

# Evolutionary Architecture

## Intent

Design for safe change over time instead of over-committing to speculative architecture.

## Principles

- Start with the simplest architecture that satisfies current known requirements.
- Preserve options where future uncertainty is high.
- Use feedback loops: tests, CI, observability, production metrics, review.
- Make changes incrementally.
- Prefer reversible decisions when uncertainty is high.
- Use architecture fitness checks when architecture properties must be protected.

## Good Practices

- Keep boundaries explicit.
- Avoid premature service extraction.
- Avoid premature generic frameworks.
- Make contracts testable.
- Use feature flags for risky behavior when appropriate.
- Use migration paths for schema and API changes.
- Document important decisions.
- Reassess architecture after real feedback.

## Review Questions

- Which decision is hard to reverse?
- Which assumption is most uncertain?
- Can we defer irreversible decisions?
- What feedback will tell us the design is wrong?
- What tests or checks protect architecture?
- What migration path exists?
- What can be rolled back?

## Anti-Patterns

- Big-design-up-front based on weak assumptions.
- Premature microservices.
- Generic plugin architecture before variation exists.
- Shared common module that becomes a dumping ground.
- Ignoring production feedback.
- Architecture docs that do not match code.
