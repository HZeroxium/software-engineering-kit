---
purpose: Mock, fake, and container boundary guidance for test isolation decisions
load-when: Choosing whether to mock, fake, or use a real or containerized dependency
tier: scenario
see-also: []
---

# Mocking Boundaries

## Mock Good Boundaries

Mocks are useful for:

- External HTTP clients.
- Email/SMS/push providers.
- Payment gateways.
- Time source.
- Random/ID generator.
- Expensive or unreliable dependencies.
- Failure injection.
- Side-effect boundaries.

## Avoid Mocking

Avoid mocking:

- Simple value objects.
- Domain logic under test.
- Repository when query behavior matters.
- Transaction behavior when transaction behavior is the risk.
- Framework behavior when integration is the risk.
- Too many internal collaborators.

## Fakes

Use fakes when:

- Behavior is simple and stable.
- You need deterministic in-memory behavior.
- A fake better expresses behavior than a mock.

## Containers

Use containers when:

- Real dependency behavior matters.
- SQL dialect matters.
- Message broker semantics matter.
- Cache expiration or serialization matters.

## Review Questions

- Does the mock hide the actual bug risk?
- Does the test verify behavior or implementation calls?
- Would a fake make the test clearer?
- Would an integration test be more appropriate?
- Are mocked failures realistic?
