# API Contracts, Versioning, and Compatibility

## Purpose

Keep backend contracts stable, explicit, and evolvable.

## Contract Elements

- Request fields.
- Response fields.
- Error model.
- Authentication context.
- Authorization behavior.
- Idempotency behavior.
- Pagination/filter/sort behavior.
- Rate limits.
- Compatibility guarantees.
- Deprecation policy.

## Backward-Compatible Changes

Usually compatible:

- Adding optional request field.
- Adding response field clients can ignore.
- Adding new error only when clients handle generic class.
- Adding new enum value only if clients tolerate unknown values.

Potentially breaking:

- Removing field.
- Renaming field.
- Changing type.
- Changing requiredness.
- Changing error semantics.
- Changing idempotency behavior.
- Changing pagination ordering.
- Returning new enum values to strict clients.

## Review Questions

- Which clients consume this contract?
- Is there a version boundary?
- Are old clients still supported?
- Does the error model change?
- Are unknown fields and enum values tolerated?
- Is migration or deprecation needed?

## Validation

- Contract tests.
- Consumer compatibility tests.
- Golden response examples.
- Schema diff review.
