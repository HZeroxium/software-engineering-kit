# Business Invariants and State Transitions

## Purpose

Make correctness explicit before designing APIs or implementation.

## Business Invariant

An invariant is a rule that must always remain true.

Examples:

- A paid order cannot be cancelled without refund workflow.
- A user cannot access another tenant’s resource.
- A completed job cannot return to pending.
- An idempotency key cannot create two different resources.

## State Transition Model

```text
Current state + command/event + guard -> next state
```

## State Transition Table

| Current   | Command / Event | Guard    | Next      | Invalid Cases |
| --------- | --------------- | -------- | --------- | ------------- |
| `<state>` | `<command>`     | `<rule>` | `<state>` | `<invalid>`   |

## Design Questions

- What are all valid states?
- Which commands/events cause transitions?
- What guards apply?
- What transitions are terminal?
- Can background jobs bypass guards?
- Which transitions require audit logging?
- Which transitions require persistence constraints?

## Review Smells

- State stored as free-form strings.
- Terminal states can be modified accidentally.
- Invalid transitions handled only in UI.
- Tests cover only happy path.
- Multiple modules implement different transition logic.
