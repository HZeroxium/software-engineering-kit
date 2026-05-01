# Bounded Contexts and Business Capabilities

## Purpose

Use bounded contexts and business capabilities to avoid mixing unrelated models and responsibilities.

## Business Capability

A business capability is something the business does, such as:

- Account management.
- Order fulfillment.
- Payment processing.
- Inventory allocation.
- Document processing.
- Notification delivery.

## Bounded Context

A bounded context defines where a model and language are valid.

The same word may mean different things in different contexts. For example, `Customer` in billing may differ from `Customer` in support.

## Design Questions

- Which capability owns this behavior?
- Which team/module/service owns the language?
- Are terms used consistently inside the boundary?
- Does this feature belong in an existing context or a new one?
- Is integration needed between contexts?

## Failure Modes

- One “common” model used by unrelated domains.
- A shared database forcing model coupling.
- One service/module owning too many capabilities.
- API contracts leaking another context’s internal model.
- Ambiguous language across teams.

## Output Pattern

```text
Capability:
<business capability>

Context boundary:
<what belongs here>

External contexts:
<integrations>

Shared language:
<terms>

Ownership concerns:
<owner/team/module/service if known>
```
