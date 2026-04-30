# Before Test Implementation Checklist

## Context

- [ ] I understand the behavior under test.
- [ ] I know the expected result.
- [ ] I know the failure mode being prevented.
- [ ] I inspected existing tests.
- [ ] I inspected test framework and build files.
- [ ] I separated facts from assumptions.

## Test Design

- [ ] I selected the narrowest useful test level.
- [ ] I know fixture/data needs.
- [ ] I know mock/fake/container boundaries.
- [ ] I identified edge cases.
- [ ] I identified negative cases.
- [ ] I identified regression case if fixing a bug.

## Commands

- [ ] I discovered test commands from repo evidence.
- [ ] I did not invent commands.
- [ ] I know how to run the narrowest relevant check.

## Safety

- [ ] Test will not use production resources.
- [ ] Test will not expose secrets.
- [ ] Test will not mutate external systems.
- [ ] High-risk validation has approval if needed.
