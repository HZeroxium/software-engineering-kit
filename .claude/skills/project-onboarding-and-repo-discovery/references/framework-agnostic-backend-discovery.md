# Framework-Agnostic Backend Discovery

## Principle

Discover backend behavior from code and configuration. Do not assume a framework or architectural style until repository evidence confirms it.

## Backend Areas to Inspect

### API Surface

Look for:

- HTTP route definitions.
- RPC services.
- Message handlers.
- CLI commands.
- Batch jobs.
- Schedulers.
- WebSocket handlers.
- GraphQL schemas/resolvers.
- Generated API code.

### Runtime Bootstrap

Look for:

- Main classes/functions.
- Server initialization.
- Module registration.
- Dependency injection setup.
- Config loading.
- Logging initialization.
- Metrics/tracing setup.
- Shutdown hooks.

### Domain and Application Logic

Look for:

- Services/use cases.
- Transaction boundaries.
- Validation.
- Error handling.
- Authorization checks.
- Business rules.
- Data access.
- External clients.

### Data Layer

Look for:

- Repositories/DAOs.
- SQL files.
- ORM mappings.
- Migrations.
- Schema definitions.
- Query builders.
- Connection pools.
- Caches.
- Data retention/deletion paths.

### Integration Layer

Look for:

- RPC clients.
- HTTP clients.
- Message producers/consumers.
- SDK wrappers.
- Retry/timeouts.
- Circuit breakers.
- Idempotency.
- Serialization/deserialization.
- Contract tests.

### Observability

Look for:

- Logging conventions.
- Metrics instrumentation.
- Tracing.
- Error reporting.
- Audit logs.
- Health checks.
- Readiness/liveness endpoints.

## Backend Safety Risks

Flag before edits:

- AuthN/AuthZ.
- Input validation.
- Secrets.
- Production config.
- Database migrations.
- Distributed transactions.
- External system writes.
- Message consumer semantics.
- Retry/idempotency behavior.
- Observability cardinality.
- Backward compatibility.
