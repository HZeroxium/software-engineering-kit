# Risk and Validation Plan

## Change Summary

-

## Risk Classification

| Risk Area        | Level           | Reason | Mitigation |
| ---------------- | --------------- | ------ | ---------- |
| Correctness      | Low/Medium/High |        |            |
| Security         | Low/Medium/High |        |            |
| Data consistency | Low/Medium/High |        |            |
| Concurrency      | Low/Medium/High |        |            |
| Performance      | Low/Medium/High |        |            |
| Observability    | Low/Medium/High |        |            |
| Compatibility    | Low/Medium/High |        |            |
| Operations       | Low/Medium/High |        |            |

## High-Risk Approval Check

Explicit approval required if the change touches:

- Database migrations.
- Data deletion or backfill.
- Authentication or authorization.
- Secrets.
- Production configs.
- CI/CD.
- Infrastructure.
- Dependency upgrades.
- Public API/schema changes.
- Destructive commands.
- Broad rewrites.

Approval needed: Yes/No  
Reason:

## Validation Plan

### Narrow Checks

-

### Broader Checks

-

### Manual Checks

-

### Observability Checks

- Logs:
- Metrics:
- Traces:
- Alerts:

## Failure Handling

If validation fails:

1. Inspect failure.
2. Classify as test issue, code issue, environment issue, or unclear.
3. Apply minimal fix only if cause is clear.
4. Rerun relevant check.
5. Escalate if cause is unclear or risk is high.

## Rollback Plan

- Immediate rollback:
- Config disable path:
- Data rollback:
- Deployment rollback:
