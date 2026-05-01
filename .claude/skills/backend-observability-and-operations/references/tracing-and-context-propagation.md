# Tracing and Context Propagation

## Purpose

Understand request and workflow flow across boundaries.

## Trace Useful Boundaries

- API entry.
- Internal use case.
- DB/query.
- External dependency call.
- Message publish.
- Message consume.
- Background job.
- AI/model call if applicable.

## Context Propagation Questions

- Is correlation ID propagated?
- Is trace context propagated across service calls?
- Is async context preserved?
- Are span attributes bounded and safe?
- Are errors attached safely?

## Failure Modes

- Trace breaks across async boundary.
- Sensitive data in span attributes.
- Too many spans for hot loop.
- Missing dependency span.
