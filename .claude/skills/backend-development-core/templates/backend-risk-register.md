# Backend Risk Register

## Task

`<backend task summary>`

## Risk Overview

- **Overall risk level:** `<low/medium/high/critical>`
- **Highest-risk category:** `<security/data/reliability/performance/ops/AI/etc.>`
- **Requires human approval before implementation:** `<yes/no>`

## Risk Register

| ID  | Risk     | Scope     | Severity                     | Likelihood          | Evidence / Trigger | Mitigation     | Owner Decision Needed? |
| --- | -------- | --------- | ---------------------------- | ------------------- | ------------------ | -------------- | ---------------------- |
| R1  | `<risk>` | `<scope>` | `<low/medium/high/critical>` | `<low/medium/high>` | `<evidence>`       | `<mitigation>` | `<yes/no>`             |
| R2  | `<risk>` | `<scope>` | `<low/medium/high/critical>` | `<low/medium/high>` | `<evidence>`       | `<mitigation>` | `<yes/no>`             |

## High-Risk Backend Areas

Check all that apply:

- [ ] AuthN/AuthZ
- [ ] Object-level authorization
- [ ] Tenant isolation
- [ ] Secrets or credentials
- [ ] Sensitive data / PII
- [ ] Production configuration
- [ ] Database schema or migrations
- [ ] Data deletion or retention
- [ ] Distributed transactions or sagas
- [ ] Messaging and duplicate processing
- [ ] External system writes
- [ ] CI/CD
- [ ] Infrastructure
- [ ] Dependency upgrades
- [ ] Generated code
- [ ] AI model calls or tool execution
- [ ] Prompt injection or AI data leakage
- [ ] Observability cardinality or sensitive logs

## Approval Gates

| Gate                   |  Required? | Reason     |
| ---------------------- | ---------: | ---------- |
| Security review        | `<yes/no>` | `<reason>` |
| Data review            | `<yes/no>` | `<reason>` |
| Architecture review    | `<yes/no>` | `<reason>` |
| Production approval    | `<yes/no>` | `<reason>` |
| Migration approval     | `<yes/no>` | `<reason>` |
| AI governance approval | `<yes/no>` | `<reason>` |

## Safe Next Step

`<recommended next step that avoids unsafe implementation>`
