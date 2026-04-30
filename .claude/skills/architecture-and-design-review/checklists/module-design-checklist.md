# Module Design Checklist

## Responsibility

- [ ] Module has a clear purpose.
- [ ] Module has one main reason to change.
- [ ] Module does not own unrelated business concepts.
- [ ] Public API is intentional.
- [ ] Internal implementation is hidden where practical.

## Dependencies

- [ ] Dependencies are acyclic.
- [ ] Dependency direction is intentional.
- [ ] Shared/common dependencies are justified.
- [ ] Infrastructure dependencies do not leak into domain logic unnecessarily.
- [ ] External provider models are mapped at boundaries.

## Data and Contracts

- [ ] Data ownership is clear.
- [ ] DTO/domain/entity boundaries are clear.
- [ ] API compatibility is considered.
- [ ] Transaction boundaries are clear.
- [ ] Invariants are protected.

## Testing

- [ ] Module can be tested independently.
- [ ] Boundary tests exist or are planned.
- [ ] Integration tests cover persistence/framework behavior where needed.
- [ ] Contract tests cover external/public boundaries where needed.

## Operations

- [ ] Important failures are observable.
- [ ] Logs avoid sensitive data.
- [ ] Metrics avoid high cardinality.
- [ ] Rollback impact is understood.
