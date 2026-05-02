---
purpose: Integration test targets, database and API checks, and anti-patterns
load-when: Testing framework, database, serialization, controller, messaging, cache, or security-filter behavior
tier: domain
see-also: []
---

# Integration Testing

## Use Integration Tests For

- Database queries.
- ORM mappings.
- Transaction behavior.
- Repository behavior.
- Serialization/deserialization.
- HTTP controllers.
- Messaging adapters.
- Cache integration.
- Framework configuration.
- Security filters.

## Good Integration Test Traits

- Uses realistic dependencies where risk exists.
- Controls test data.
- Cleans up data safely.
- Avoids reliance on test order.
- Verifies persisted state when relevant.
- Verifies transaction and rollback behavior.
- Uses fake or containerized external dependencies when appropriate.

## Database Integration Tests

Check:

- Constraints.
- Index assumptions.
- Query filters.
- Soft delete behavior.
- Pagination.
- Sorting.
- Transaction boundaries.
- Duplicate handling.
- Migration compatibility.

## Web/API Integration Tests

Check:

- Request validation.
- Response status.
- Response body.
- Error mapping.
- Authentication and authorization.
- Serialization format.
- Backward compatibility.

## Avoid

- Calling uncontrolled external services.
- Sharing mutable state across tests.
- Depending on local developer machine state.
- Hiding database behavior behind excessive mocks.
- Slow broad tests when a narrower test proves the behavior.
