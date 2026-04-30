# Microservices

## Intent

Split a system into independently deployable services aligned around business capabilities and ownership boundaries.

## Use Microservices When

- Service ownership boundaries are clear.
- Independent deployment is valuable.
- Teams can own services end-to-end.
- Scalability or reliability requirements differ by capability.
- Data ownership can be separated.
- Operational maturity exists.

## Avoid Microservices When

- The domain boundaries are unclear.
- The team is small and deployment independence is not needed.
- Shared database is still required.
- Distributed transactions would dominate the design.
- Observability, CI/CD, and incident response are weak.
- A modular monolith would solve the problem with less complexity.

## Review Questions

- What business capability does the service own?
- What data does it own?
- Does another service write its data?
- What are its synchronous APIs?
- What events does it publish/consume?
- What is the consistency model?
- What happens when dependencies fail?
- How is backward compatibility maintained?
- How is the service observed?
- How is it deployed and rolled back?

## Common Risks

- Distributed monolith.
- Chatty synchronous calls.
- Shared database coupling.
- Poor service ownership.
- Contract drift.
- Inconsistent data without reconciliation.
- Retry storms.
- Missing idempotency.
- Poor observability.
