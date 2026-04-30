# Architecture Review Checklist

## Context

- [ ] Problem and goals are clear.
- [ ] Non-goals are clear.
- [ ] Constraints are clear.
- [ ] Current architecture is understood or assumptions are stated.
- [ ] Stakeholders or consumers are identified.

## Boundaries

- [ ] Module/service responsibilities are clear.
- [ ] Dependency direction is intentional.
- [ ] API boundaries are stable.
- [ ] Persistence boundaries are clear.
- [ ] Data ownership is clear.
- [ ] External integration boundaries are clear.

## Quality Attributes

- [ ] Correctness risks are addressed.
- [ ] Security and privacy risks are addressed.
- [ ] Data consistency model is defined.
- [ ] Concurrency risks are considered.
- [ ] Failure modes are considered.
- [ ] Performance and scalability are considered.
- [ ] Observability is considered.
- [ ] Testability is considered.
- [ ] Maintainability is considered.

## Evolution

- [ ] Migration path exists.
- [ ] Rollback or disable path exists.
- [ ] Decisions are reversible where possible.
- [ ] Important decisions are documented.
- [ ] Over-engineering is avoided.

## Validation

- [ ] Tests are identified.
- [ ] Contract checks are identified.
- [ ] Build/typecheck/lint/static-analysis commands are discovered from repo if needed.
- [ ] Manual review is recommended for high-risk areas.
