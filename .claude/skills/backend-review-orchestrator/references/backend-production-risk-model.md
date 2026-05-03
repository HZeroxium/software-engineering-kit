---
purpose: High-risk backend areas and production failure mode table for prioritizing review scrutiny
load-when: Prioritizing which areas require deeper scrutiny, stronger tests, or explicit human review
tier: domain
see-also: []
---

# Backend Production Risk Model

## High-Risk Areas

- Authentication and authorization.
- Object-level access control.
- Tenant isolation.
- Secrets and credentials.
- Sensitive data and logs.
- Database migrations.
- Data deletion and retention.
- Distributed workflows.
- External provider calls.
- Messaging and duplicate processing.
- Production configuration.
- CI/CD and infrastructure.
- Dependency upgrades.
- Generated code.
- AI model calls and tool execution.

## Production Failure Modes

| Area          | Failure Mode                                                          |
| ------------- | --------------------------------------------------------------------- |
| Security      | Unauthorized access, privilege escalation, secret leak                |
| Data          | Loss, corruption, duplicate writes, cross-tenant leakage              |
| Integration   | Retry storm, timeout cascade, duplicate side effects                  |
| Reliability   | Outage, cascading failure, missing fallback                           |
| Performance   | Latency spike, resource exhaustion, hot partition                     |
| Observability | Incident cannot be detected or diagnosed                              |
| Operations    | Bad deploy cannot be rolled back                                      |
| AI            | Hallucinated output, prompt injection, data leakage, unsafe tool call |

## Review Implication

Any change in these areas should receive higher scrutiny, stronger tests, and clearer human approval boundaries.
