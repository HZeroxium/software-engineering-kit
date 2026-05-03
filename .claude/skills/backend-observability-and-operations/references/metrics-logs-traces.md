---
purpose: Three observability signal types (metrics, logs, traces) and the 4 operator questions that guide signal selection
load-when: Starting any observability review — load first to establish signal vocabulary before loading domain references
tier: foundational
see-also:
  - structured-logging.md
  - metrics-design-and-cardinality.md
  - tracing-and-context-propagation.md
  - alerting-and-runbooks.md
  - observability-review-workflow.md
---

# Metrics, Logs, and Traces

## Metrics

Best for aggregate trends:

- Request rate.
- Error rate.
- Duration.
- Saturation.
- Backlog.
- Business counters.

## Logs

Best for discrete events and diagnosis:

- Request outcomes.
- State transitions.
- Failure context.
- Security/audit events.
- Job lifecycle events.

## Traces

Best for request/workflow path:

- Cross-service calls.
- Dependency latency.
- Async propagation.
- Root-cause diagnosis.

## Review Question

Can operators answer:

1. Is it broken?
2. Who is affected?
3. Why is it broken?
4. What should we do?
