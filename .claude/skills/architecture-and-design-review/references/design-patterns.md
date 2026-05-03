---
purpose: Common structural and behavioral patterns (Strategy, Factory, Adapter, Repository, etc.) with applicability criteria
load-when: Evaluating whether a design pattern solves a recurring structural or behavioral force
tier: domain
see-also:
  - api-contracts-and-boundaries.md
---

# Design Patterns

## Principle

Use design patterns to solve recurring design forces. Do not introduce patterns for appearance.

## Common Useful Patterns

### Strategy

Use when behavior varies by policy, type, provider, or algorithm.

Avoid when a simple conditional is clearer and variation is unlikely.

### Factory

Use when construction is complex, conditional, or must hide implementation choices.

Avoid when constructor or simple builder is enough.

### Adapter

Use when integrating external APIs or translating incompatible interfaces.

Good for isolating third-party SDKs, HTTP clients, and provider-specific models.

### Facade

Use when simplifying a complex subsystem behind a stable API.

Avoid hiding important failure modes.

### Template Method

Use when steps are fixed but some steps vary.

Avoid when inheritance creates tight coupling.

### Observer / Pub-Sub

Use when multiple independent listeners react to an event.

Consider event-driven architecture risks: ordering, idempotency, retry, observability.

### Repository

Use when isolating persistence details.

Avoid pretending repository methods are business operations.

### Specification

Use when business rules need composition and reuse.

Avoid overly abstract rule engines too early.

## Review Questions

- What problem does the pattern solve?
- Is variation real or speculative?
- Does the pattern reduce coupling?
- Does it improve testability?
- Does it hide important behavior?
- Is the pattern consistent with repo conventions?
- Could a simpler design work?
