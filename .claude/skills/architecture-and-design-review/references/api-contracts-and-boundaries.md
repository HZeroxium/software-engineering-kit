---
purpose: API contract review dimensions — compatibility, error model, versioning, DTO boundaries — across all boundary types
load-when: Reviewing or designing any public/internal API, event schema, module interface, or service contract
tier: domain
see-also: []
---

# API Contracts and Boundaries

## API Boundary Types

- Public external API.
- Internal service API.
- Module API.
- Event schema.
- Database schema.
- CLI/script interface.
- Function/class interface.

## Contract Review

Check:

- Inputs.
- Outputs.
- Error model.
- Status codes.
- Validation rules.
- Authentication and authorization.
- Pagination and limits.
- Idempotency.
- Versioning.
- Backward compatibility.
- Deprecation strategy.
- Observability fields.

## DTO / Domain / Entity Boundaries

Prefer clear separation when useful:

- DTO: external API shape.
- Domain model: business concepts and invariants.
- Entity: persistence representation.
- View model: UI-facing representation.
- Event model: durable published fact.

Avoid accidental leakage:

- Persistence entity directly exposed as API response.
- API DTO used as domain object.
- External provider model used throughout core logic.
- Internal error exposed to client.

## Compatibility

Breaking changes include:

- Removing fields.
- Renaming fields.
- Changing field meaning.
- Changing required/optional status.
- Changing enum behavior.
- Changing error shape.
- Changing authentication requirements.
- Changing pagination semantics.

## Review Questions

- Who owns this contract?
- Who consumes it?
- Is the error model stable?
- Are unknown fields tolerated?
- Is versioning needed?
- Are compatibility tests needed?
- Is documentation updated?
