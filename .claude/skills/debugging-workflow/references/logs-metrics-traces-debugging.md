---
purpose: Logs, metrics, traces, correlation, and observability gap analysis
load-when: Debugging runtime symptoms, production symptoms, operational signals, or observability data
tier: domain
see-also: []
---

# Logs, Metrics, and Traces Debugging

## Logs

Use logs to answer:

- What happened?
- When did it happen?
- Which request/job/user-safe ID was involved?
- Which dependency failed?
- What error class occurred?
- Was retry attempted?
- Was fallback used?

Check:

- Correlation ID.
- Request ID.
- Trace ID.
- Safe entity IDs.
- Error class.
- Status code.
- Duration.
- Retry count.
- Dependency name.

Avoid exposing:

- Secrets.
- Tokens.
- Credentials.
- Customer data.
- Sensitive payloads.

## Metrics

Use metrics to answer:

- How often is this happening?
- When did it start?
- Is it correlated with deploy?
- Is latency rising?
- Is error rate rising?
- Is saturation occurring?
- Is queue lag increasing?

Useful metric groups:

- Request rate.
- Error rate.
- Latency.
- Saturation.
- Queue depth/lag.
- Retry count.
- Timeout count.
- External dependency errors.

## Traces

Use traces to answer:

- Where is time spent?
- Which downstream dependency failed?
- Which span returned error?
- Are retries visible?
- Is context propagated?
- Are parallel operations behaving as expected?

## Correlation

Correlate:

- Deploy time.
- Config change.
- Traffic spike.
- Dependency outage.
- Error rate.
- Latency.
- Logs for same trace/request.
- CI or test failures.

## Observability Gaps

Call out when debugging is blocked by:

- Missing correlation IDs.
- Missing structured logs.
- Missing metrics.
- High-cardinality or noisy metrics.
- Missing traces.
- Redacted too much or too little.
