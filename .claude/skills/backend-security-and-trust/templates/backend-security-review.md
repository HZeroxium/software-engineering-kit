# Backend Security Review

## Summary

- **Review target:** `<feature/API/diff/module>`
- **Risk level:** `<low/medium/high/critical>`
- **Recommendation:** `<approve / revise / block>`
- **Manual security review required:** `<yes/no>`

## Trust Boundaries

| Boundary     | Actor / System   | Trust Level                             | Notes     |
| ------------ | ---------------- | --------------------------------------- | --------- |
| `<boundary>` | `<actor/system>` | `<trusted/untrusted/partially trusted>` | `<notes>` |

## Authentication

| Caller     | Identity Proof                          | Risk     |
| ---------- | --------------------------------------- | -------- |
| `<caller>` | `<token/session/service identity/etc.>` | `<risk>` |

## Authorization

| Action     | Resource     | Required Permission | Check Location | Risk     |
| ---------- | ------------ | ------------------- | -------------- | -------- |
| `<action>` | `<resource>` | `<permission>`      | `<layer/code>` | `<risk>` |

## Object-Level / Tenant Access

| Resource     | Owner / Tenant Boundary | Check     | Gap     |
| ------------ | ----------------------- | --------- | ------- |
| `<resource>` | `<owner/tenant>`        | `<check>` | `<gap>` |

## Sensitive Data

| Data     | Source     | Sink                          | Protection     |
| -------- | ---------- | ----------------------------- | -------------- |
| `<data>` | `<source>` | `<API/log/event/db/provider>` | `<protection>` |

## Secrets and Config

- `<risk>`
- `<risk>`

## Input / Output Security

- `<injection/SSRF/deserialization/output leakage/etc.>`

## Abuse Cases

- `<abuse case>`

## Audit Logging

- `<security-relevant event>`

## Findings

### Blocking

- `<finding>`

### Important

- `<finding>`

### Optional

- `<finding>`

## Validation

- `<access-control test>`
- `<tenant isolation test>`
- `<secret scanning/manual review>`
- `<abuse/rate limit test>`
