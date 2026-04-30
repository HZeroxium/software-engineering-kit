# Generated Test Review Checklist

## Grounding

- [ ] Test uses real project APIs.
- [ ] Test imports compile in this repo.
- [ ] Test framework matches existing project.
- [ ] Test command is discovered, not invented.
- [ ] Test data matches actual domain model.
- [ ] Test does not invent behavior.

## Behavior

- [ ] Test verifies meaningful behavior.
- [ ] Test covers happy path.
- [ ] Test covers relevant negative path.
- [ ] Test covers edge case.
- [ ] Regression test fails before fix when applicable.
- [ ] Assertions are strong enough.

## Isolation

- [ ] Test is deterministic.
- [ ] Test does not depend on execution order.
- [ ] Test does not depend on real external systems.
- [ ] Test cleans up data.
- [ ] Time/randomness is controlled.

## Mocking

- [ ] Mocks are at appropriate boundaries.
- [ ] Mocks do not hide integration risk.
- [ ] Interactions are not over-specified.
- [ ] Failure behavior is realistic.

## Safety

- [ ] Test does not expose secrets.
- [ ] Test does not use production resources.
- [ ] Test does not mutate external systems.
- [ ] Test fixtures contain no sensitive data.
