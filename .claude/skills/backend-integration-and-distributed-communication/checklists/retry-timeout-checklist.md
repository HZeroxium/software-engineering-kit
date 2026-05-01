# Retry and Timeout Checklist

- [ ] Remote call timeout defined.
- [ ] Caller deadline considered.
- [ ] Retryable errors classified.
- [ ] Non-retryable errors classified.
- [ ] Retry limit defined.
- [ ] Backoff/jitter considered.
- [ ] Idempotency confirmed before retrying writes.
- [ ] Retry storm risk considered.
- [ ] Dependency overload behavior considered.
- [ ] Metrics/logs for retries planned.
