# Cache Correctness Checklist

- [ ] Source of truth identified.
- [ ] Cache key includes tenant/user if needed.
- [ ] Sensitive data handling checked.
- [ ] Staleness tolerance defined.
- [ ] Invalidation strategy defined.
- [ ] TTL justified.
- [ ] Stampede risk checked.
- [ ] Cache-unavailable behavior defined.
- [ ] Authorization-dependent data not leaked.
- [ ] Tests cover invalidation and isolation.
