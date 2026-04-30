# Immutability and State

## Principle

Prefer immutable data when ownership, lifecycle, or concurrency could be unclear.

## Use Immutability For

- Value objects.
- Commands.
- Queries.
- DTOs.
- Events.
- Configuration.
- Test fixtures.
- Shared data across threads/tasks.
- Domain states where mutation would hide transitions.

## Mutable State Is Acceptable When

- Ownership is clear.
- Lifecycle is controlled.
- Mutation improves clarity.
- Performance requires it and is measured.
- Framework requires it.
- State transitions are explicit.

## Risks of Mutable State

- Hidden side effects.
- Race conditions.
- Test order dependence.
- Hard-to-debug state corruption.
- Accidental shared references.
- Cache inconsistency.

## Java

- Prefer final fields where practical.
- Use records only when supported by project Java version and conventions.
- Use defensive copies for mutable collections crossing boundaries.
- Avoid exposing mutable internals.

## Python

- Use frozen dataclasses where useful.
- Avoid mutable default arguments.
- Copy mutable input when ownership is unclear.
- Make mutation explicit.

## TypeScript

- Use readonly types where useful.
- Avoid mutating inputs unless documented.
- Prefer immutable updates in UI state.
- Avoid shared mutable module state.
