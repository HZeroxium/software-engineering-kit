---
purpose: Java-specific illustrative patterns for structured logging, metrics, and tracing — concepts only, not prescriptive APIs
load-when: Working in a Java codebase and need concrete observability pattern examples to calibrate approach
tier: scenario
see-also: []
---

# Java Observability Patterns

Examples are illustrative only. Follow repository conventions and internal observability libraries.

## Structured Log Concept

```java
logger.info("document_job_submitted",
    kv("jobId", safeJobId),
    kv("outcome", "accepted"),
    kv("durationMs", durationMs)
);
```

## Metric Concept

```text
Counter: document_job_submitted_total
Labels: outcome, operation
Avoid: userId, requestId, raw documentName
```

## Trace Concept

```text
Span: DocumentSubmitUseCase.execute
Attributes:
- operation=document_submit
- outcome=accepted|rejected|failed
Avoid sensitive document content.
```

## Notes

- Do not invent metric names if repo conventions exist.
- Do not add high-cardinality labels.
- Do not log sensitive payloads.
- Discover the actual logging/metrics/tracing library from repo imports before applying any pattern.
