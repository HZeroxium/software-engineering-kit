# Backend Design Checklist

## Problem and Scope

- [ ] Feature intent is clear.
- [ ] Actor and business capability are clear.
- [ ] Current and desired behavior are clear.
- [ ] Out-of-scope items are listed.
- [ ] Primary backend scope is selected.

## Domain and API

- [ ] Domain concepts are identified.
- [ ] Business rules are listed.
- [ ] State transitions are listed where applicable.
- [ ] API/interface type is selected.
- [ ] Request/response/event contract is sketched.
- [ ] Error model is defined.
- [ ] Idempotency requirement is checked.
- [ ] Compatibility/versioning impact is checked.

## Application Workflow

- [ ] Use-case flow is described.
- [ ] Transaction boundary is identified.
- [ ] Side effects are identified.
- [ ] Async work is identified.
- [ ] Failure and compensation behavior is described.

## Data

- [ ] Data ownership is clear.
- [ ] Reads/writes are identified.
- [ ] Schema/index/migration impact is checked.
- [ ] Consistency requirements are defined.
- [ ] Cache impact is checked.
- [ ] Data lifecycle impact is checked.

## Security and Trust

- [ ] Authentication assumptions are clear.
- [ ] Authorization checks are clear.
- [ ] Object-level access control is checked.
- [ ] Tenant isolation is checked.
- [ ] Secrets/sensitive data are checked.
- [ ] Audit logging is checked.

## Integration and Operations

- [ ] External/internal integrations are listed.
- [ ] Timeouts/retries are defined.
- [ ] Duplicate handling is defined.
- [ ] Reliability and fallback behavior are defined.
- [ ] Performance assumptions are stated.
- [ ] Observability requirements are defined.

## Validation

- [ ] Unit tests planned.
- [ ] Integration tests planned.
- [ ] Contract tests planned if needed.
- [ ] Security tests/review planned if needed.
- [ ] Performance/resilience tests planned if needed.
- [ ] Validation evidence is defined.
