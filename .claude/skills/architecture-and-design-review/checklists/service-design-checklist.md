# Service Design Checklist

## Ownership

- [ ] Service owns a clear business capability.
- [ ] Service owns its data or data ownership is explicit.
- [ ] Team ownership is clear.
- [ ] Runtime responsibility is clear.

## API

- [ ] API contract is clear.
- [ ] Error model is defined.
- [ ] Authentication and authorization are defined.
- [ ] Compatibility strategy is defined.
- [ ] Rate limits or abuse controls are considered.

## Data

- [ ] Source of truth is defined.
- [ ] Transaction model is defined.
- [ ] Consistency model is defined.
- [ ] Migration plan exists if data changes.
- [ ] Rollback plan exists if data changes.

## Failure Handling

- [ ] Timeouts are considered.
- [ ] Retries are bounded and safe.
- [ ] Idempotency is considered.
- [ ] Partial failure behavior is defined.
- [ ] Dependency failure behavior is defined.

## Observability

- [ ] Logs are structured and safe.
- [ ] Metrics cover rate, errors, latency, saturation.
- [ ] Traces are considered for distributed flows.
- [ ] Alerts/dashboards are considered for production behavior.

## Delivery

- [ ] Deployment impact is understood.
- [ ] CI/CD impact is understood.
- [ ] Rollout strategy is defined.
- [ ] Manual review is planned for high-risk changes.
