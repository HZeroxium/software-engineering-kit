# Test-First or Test-Aware Implementation

## Principle

Backend implementation should be test-aware even when not strictly test-first.

## When to Prefer Test-First

- Business rule changes.
- State transition changes.
- Bug fixes with known reproduction.
- Idempotency behavior.
- Authorization rules.
- Data consistency logic.
- Pure domain/application logic.

## When to Implement Then Test

- Integration wiring.
- Observability instrumentation.
- Configuration behavior.
- Tests require discovering repository harness.
- Legacy code lacks seams and requires minimal safe change first.

## Test Selection

| Change Type      | Recommended Tests                              |
| ---------------- | ---------------------------------------------- |
| Domain rule      | Unit/domain tests                              |
| API contract     | Contract/API tests                             |
| Persistence      | Integration tests                              |
| Migration        | Migration compatibility tests                  |
| External client  | Adapter tests with fake/mock server            |
| Message consumer | Duplicate/retry/failure tests                  |
| Authorization    | Access-control tests                           |
| Observability    | Metrics/logs/traces assertion or manual review |
| Performance      | Benchmark/load test if risk warrants           |

## Test Quality

Good backend tests:

- Assert behavior, not implementation details.
- Cover edge cases and failure modes.
- Avoid brittle timing.
- Avoid over-mocking critical integrations.
- Use existing fixtures/builders.
- Are deterministic.
