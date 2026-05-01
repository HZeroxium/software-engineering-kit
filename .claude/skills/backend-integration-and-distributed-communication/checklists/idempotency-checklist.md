# Idempotency Checklist

- [ ] Operation may be retried or duplicated.
- [ ] Side effects identified.
- [ ] Idempotency key defined.
- [ ] Deduplication scope defined.
- [ ] Deduplication storage defined.
- [ ] Concurrent duplicate handling defined.
- [ ] Duplicate response behavior defined.
- [ ] Retention window defined.
- [ ] Tests cover duplicate and retry cases.
