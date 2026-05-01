# Authorization Boundary Review

## Operation

`<operation/API/use case>`

## Caller

`<user/service/admin/job/etc.>`

## Resource

`<resource>`

## Authorization Model

- **Model:** `<RBAC/ABAC/ReBAC/policy/custom/unknown>`
- **Permission:** `<permission>`
- **Ownership field:** `<owner/tenant/account/etc.>`
- **Check location:** `<API/application/domain/data layer>`

## Object-Level Access Control

| Resource ID Source             | Ownership Verified? | Risk     |
| ------------------------------ | ------------------: | -------- |
| `<path/query/body/message/db>` |  `<yes/no/unknown>` | `<risk>` |

## Tenant Isolation

| Area              | Tenant Boundary Applied? | Notes     |
| ----------------- | -----------------------: | --------- |
| API               |       `<yes/no/unknown>` | `<notes>` |
| Application logic |       `<yes/no/unknown>` | `<notes>` |
| Query             |       `<yes/no/unknown>` | `<notes>` |
| Cache             |       `<yes/no/unknown>` | `<notes>` |
| Logs/audit        |       `<yes/no/unknown>` | `<notes>` |

## Findings

- `<finding>`

## Minimal Fix

`<fix>`

## Tests

- `<allowed actor test>`
- `<denied actor test>`
- `<cross-tenant access test>`
