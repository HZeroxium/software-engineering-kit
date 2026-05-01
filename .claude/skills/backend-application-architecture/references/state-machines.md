# State Machines

## Purpose

Use explicit state machines when lifecycle rules matter.

## Use When

- Entity has meaningful lifecycle.
- Invalid transitions are dangerous.
- Multiple actors can update state.
- Async jobs update progress.
- Auditability matters.

## Design Elements

- States.
- Events/commands.
- Guards.
- Transitions.
- Terminal states.
- Side effects.
- Persistence and concurrency control.

## Review Smells

- Status changed directly from many places.
- Terminal state modified later.
- No tests for invalid transitions.
- State transition and side effects are mixed.
- Concurrent transitions not considered.
