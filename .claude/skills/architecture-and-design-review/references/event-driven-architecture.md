---
purpose: Event design principles (naming, versioning, idempotency, ordering, reliability) and common EDA patterns
load-when: Design involves async messaging, event publishing/consuming, or event-driven workflows
tier: scenario
see-also:
  - api-contracts-and-boundaries.md
---

# Event-Driven Architecture

## Intent

Use events to decouple producers and consumers, model business facts, and support asynchronous workflows.

## Good Fit

Use when:

- Multiple consumers react to the same business fact.
- Work can be asynchronous.
- Producer should not know all consumers.
- Cross-service workflows need loose coupling.
- Audit/event history is useful.
- Backpressure and buffering are needed.

## Poor Fit

Avoid when:

- Immediate response is required.
- Strong consistency is mandatory across boundaries.
- Event ownership is unclear.
- Consumers require too much hidden context.
- Debuggability and observability are weak.

## Event Design

Good events should be:

- Named as past-tense business facts.
- Versioned where necessary.
- Stable enough for consumers.
- Clear about source of truth.
- Free of unnecessary sensitive data.
- Idempotent to consume.
- Compatible with replay if replay is expected.

## Review Questions

- Is this an event or a command?
- Who owns the event schema?
- What guarantees exist: at-most-once, at-least-once, ordering?
- Are consumers idempotent?
- What happens on duplicate delivery?
- What happens on delayed delivery?
- What happens when consumer processing fails?
- Is there a dead-letter or retry strategy?
- Are events emitted after durable state changes?
- Is observability sufficient?

## Common Patterns

- Outbox pattern for reliable event publishing.
- Inbox/deduplication for idempotent consumption.
- Saga/process manager for long-running workflows.
- Dead-letter queue for poison messages.
- Schema versioning for compatibility.
