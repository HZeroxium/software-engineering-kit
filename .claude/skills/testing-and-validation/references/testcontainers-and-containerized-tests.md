---
purpose: Containerized test fit, risks, and review questions for real dependency behavior
load-when: Real dependency behavior matters, such as SQL dialects, brokers, caches, or protocol emulators
tier: scenario
see-also: []
---

# Testcontainers and Containerized Tests

## Use Containerized Tests When

- Real database behavior matters.
- SQL dialect differences matter.
- Index/constraint behavior matters.
- Transaction behavior matters.
- Message broker behavior matters.
- Cache behavior matters.
- Local mocks are too unrealistic.

## Good Fit

- PostgreSQL/MySQL integration tests.
- Kafka/RabbitMQ integration tests.
- Redis integration tests.
- Search engine integration tests.
- External service protocol emulators.

## Risks

- Slower tests.
- Docker availability.
- CI environment constraints.
- Flaky startup.
- Resource usage.
- Test data cleanup.

## Good Practices

- Reuse containers according to project convention.
- Keep fixtures minimal.
- Wait for readiness deterministically.
- Clean up test data.
- Avoid depending on local machine state.
- Make failure logs diagnosable.
- Keep containerized tests focused.

## Review Questions

- Is a container needed, or would a unit test suffice?
- Does the test validate real behavior that mocks would miss?
- Is the test deterministic in CI?
- Are startup and cleanup reliable?
- Is test scope narrow enough?
