# Observability Checklist

Use this as a **scope-level gate**: are all signals accounted for at the feature or release level?
For signal-specific depth, use `logging-checklist.md`, `metrics-checklist.md`, and `tracing-checklist.md`.

- [ ] User-visible behavior identified.
- [ ] Failure modes identified.
- [ ] Logs planned.
- [ ] Metrics planned.
- [ ] Traces planned where useful.
- [ ] Alerts considered.
- [ ] Runbook considered.
- [ ] Correlation ID considered.
- [ ] Sensitive data excluded.
- [ ] Cardinality risk checked.
- [ ] Validation plan exists.
