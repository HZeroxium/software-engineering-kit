---
purpose: Tenant isolation models, missing predicate failure modes, background job tenant awareness, cache key isolation
load-when: Reviewing multi-tenant data access, tenant-scoped queries, or isolation design
tier: domain
see-also: []
---

# Multi-Tenancy Data Isolation

## Purpose

Prevent cross-tenant access and noisy-neighbor risks.

## Isolation Models

- Shared table with tenant ID.
- Separate schema per tenant.
- Separate database per tenant.
- Separate service/environment per tenant.

## Questions

- How is tenant identity established?
- Is tenant ID part of every query?
- Is tenant ID part of cache key?
- Are unique constraints tenant-scoped?
- Are background jobs tenant-aware?
- Are metrics/logs safe for tenant context?

## Failure Modes

- Missing tenant predicate.
- Tenant ID accepted from untrusted input.
- Shared cache key leaks data.
- Background worker ignores tenant.
- Admin APIs bypass tenant checks without audit.
