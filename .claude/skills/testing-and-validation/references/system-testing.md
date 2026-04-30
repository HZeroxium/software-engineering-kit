# System Testing

## Use System Tests For

- Critical user flows.
- Cross-service workflows.
- Deployment-like scenarios.
- End-to-end API behavior.
- High-risk release validation.
- Incident regression validation.

## Good System Test Traits

- Tests a business-relevant workflow.
- Uses stable test data.
- Has clear pass/fail criteria.
- Avoids brittle timing assumptions.
- Has strong cleanup.
- Produces diagnosable failure output.
- Runs in controlled environments.

## Validate

- Happy path.
- Permission behavior.
- Failure behavior.
- Retry behavior.
- Data consistency.
- User-visible result.
- Observability signals where relevant.

## Avoid

- Overusing system tests for logic better tested at lower levels.
- Testing implementation details.
- Depending on third-party services without isolation.
- Long sleeps instead of deterministic waits.
- Broad tests that fail for unrelated reasons.
