# Java Logging / Metrics / Tracing Review Example

## Scenario

A Java backend adds asynchronous document processing.

## Findings

### Important — Missing Job Lifecycle Metrics

- **Risk:** Operators cannot detect stuck or failing jobs.
- **Minimal fix:** Add metrics for submitted, completed, failed, and processing duration using existing repo metrics conventions.
- **Validation:** Manual metrics review or test if telemetry test utilities exist.

### Important — Logs Lack Correlation Context

- **Risk:** Production debugging cannot correlate submit request with worker processing.
- **Minimal fix:** Include safe correlation/job ID fields in submit and worker logs.
- **Validation:** Log review.

### Blocking — Sensitive Document Content Logged

- **Risk:** Sensitive data leakage.
- **Minimal fix:** Remove raw content from logs; log only safe identifiers.
- **Validation:** Test or manual grep/log review.

## Notes

- Do not invent metrics library APIs.
- Follow existing internal observability wrappers.
- Avoid userId/requestId as metric labels.
