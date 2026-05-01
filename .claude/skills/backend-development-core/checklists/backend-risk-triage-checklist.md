# Backend Risk Triage Checklist

## Security and Trust

- [ ] Authentication affected.
- [ ] Authorization affected.
- [ ] Object-level authorization affected.
- [ ] Tenant isolation affected.
- [ ] Secrets or credentials involved.
- [ ] Sensitive data or PII involved.
- [ ] Audit logging required.
- [ ] Abuse/rate limiting relevant.
- [ ] Threat model needed.

## Data and Persistence

- [ ] Schema changes involved.
- [ ] Migration involved.
- [ ] Transaction boundaries changed.
- [ ] Consistency assumptions changed.
- [ ] Query/index performance affected.
- [ ] Cache correctness affected.
- [ ] Data retention/deletion affected.
- [ ] Multi-tenancy affected.

## Distributed Systems

- [ ] External API involved.
- [ ] RPC involved.
- [ ] Messaging/events involved.
- [ ] Retry/timeout behavior involved.
- [ ] Idempotency required.
- [ ] Duplicate delivery possible.
- [ ] Outbox/inbox needed.
- [ ] Backpressure or circuit breaker relevant.

## Reliability and Operations

- [ ] SLO/SLI affected.
- [ ] Availability affected.
- [ ] Fallback/degradation needed.
- [ ] Health check affected.
- [ ] Runbook needed.
- [ ] Alert needed.
- [ ] Rollback plan needed.
- [ ] Production config affected.
- [ ] CI/CD affected.
- [ ] Infrastructure affected.

## Performance and Cost

- [ ] Latency target affected.
- [ ] Throughput affected.
- [ ] p95/p99 relevant.
- [ ] Database load affected.
- [ ] Concurrency/resource pool affected.
- [ ] Cache cost or telemetry cost affected.
- [ ] AI token/model cost affected.
- [ ] Load testing needed.

## AI and Governance

- [ ] AI model/provider involved.
- [ ] Prompt/context/RAG involved.
- [ ] Tool calling or agents involved.
- [ ] AI evaluation needed.
- [ ] Prompt injection risk.
- [ ] Data leakage risk.
- [ ] Compliance or privacy review needed.
- [ ] Human approval boundary needed.

## Risk Level Decision

- **Low:** Local, reversible, no data/security/production impact.
- **Medium:** Affects behavior or integration but has clear tests and rollback.
- **High:** Affects security, data, production config, migrations, distributed workflows, or reliability.
- **Critical:** May expose secrets/PII, break authorization, mutate production data, cause outage, or bypass human approval.
