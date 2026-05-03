---
purpose: Core domain modeling vocabulary — entity, value object, aggregate, domain service, domain event, invariant, command, query
load-when: Domain modeling, entity/value object/aggregate design, or core domain vocabulary needed
tier: foundational
see-also:
  - bounded-contexts-and-business-capabilities.md
  - business-invariants-and-state-transitions.md
---

# Domain Modeling

## Purpose

Model backend behavior around business concepts rather than framework classes, endpoints, or tables.

## Core Concepts

- **Entity:** Has identity and lifecycle.
- **Value Object:** Immutable descriptive value without identity.
- **Aggregate:** Consistency boundary around related entities.
- **Domain Service:** Domain operation that does not naturally belong to one entity.
- **Domain Event:** Business fact that happened.
- **Invariant:** Rule that must always hold.
- **Command:** Intent to change state.
- **Query:** Request to read state.

## Design Questions

- What business capability is being modeled?
- What concepts have identity?
- What values should be immutable?
- What rules must always hold?
- Which state transitions are valid?
- What event names describe facts, not commands?
- Which behavior belongs in the domain vs application layer?

## Review Smells

- Domain logic in controllers or transport handlers.
- Entities as passive records with all rules elsewhere.
- Generic names like `Manager`, `Processor`, `DataService`.
- Database table names driving business language.
- Missing invariants or state transition rules.
- Domain objects depending on infrastructure APIs.

## Java Examples

See `java-domain-modeling-examples.md` when Java code examples are explicitly requested.
