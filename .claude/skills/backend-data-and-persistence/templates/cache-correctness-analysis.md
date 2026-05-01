# Cache Correctness Analysis

## Cached Data

`<data>`

## Cache Purpose

- [ ] Reduce latency
- [ ] Reduce database load
- [ ] Avoid repeated external call
- [ ] Share computed result
- [ ] Other: `<purpose>`

## Source of Truth

`<database/service/provider/etc.>`

## Cache Key

`<key structure>`

## Invalidation / Refresh Strategy

| Trigger                           | Action                       | Risk     |
| --------------------------------- | ---------------------------- | -------- |
| `<write/update/delete/event/TTL>` | `<invalidate/update/expire>` | `<risk>` |

## Staleness

- **Allowed stale reads:** `<yes/no>`
- **Maximum stale duration:** `<duration>`
- **User-visible impact:** `<impact>`

## Multi-Tenancy / Authorization

- **Tenant/user in key:** `<yes/no>`
- **Authorization-dependent data cached:** `<yes/no>`
- **Leakage risk:** `<risk>`

## Failure Modes

- `<stampede>`
- `<stale data>`
- `<wrong tenant/user data>`
- `<cache unavailable>`

## Validation

- `<cache hit/miss test>`
- `<invalidation test>`
- `<tenant isolation test>`
- `<fallback test>`
