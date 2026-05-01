# Event Contracts

## Purpose

Keep event contracts stable and safe for distributed consumers.

## Event Design Rules

- Name events as facts, not commands.
- Include stable identifiers.
- Include occurred-at timestamp.
- Include producer/schema version where applicable.
- Minimize sensitive data.
- Make optional fields truly optional.
- Avoid leaking internal database shape.
- Document ordering and duplicate expectations.

## Compatibility

Usually compatible:

- Add optional field.
- Add new event type consumers can ignore.

Potentially breaking:

- Remove field.
- Rename field.
- Change field meaning.
- Change identifier semantics.
- Add required field.
- Change ordering assumptions.

## Validation

- Producer contract test.
- Consumer contract test.
- Schema compatibility check.
- Replay test if supported.
