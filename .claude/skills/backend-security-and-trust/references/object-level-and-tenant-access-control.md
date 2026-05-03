---
purpose: Object ownership verification and tenant isolation required checks
load-when: Task involves resource ownership, tenant isolation, or multi-tenant data access
tier: domain
see-also: []
---

# Object-Level and Tenant Access Control

## Purpose

Prevent users or tenants from accessing resources they do not own.

## Required Checks

- Resource ID source is untrusted if provided by caller.
- Resource ownership must be verified.
- Tenant boundary must be applied to queries.
- Cache key must include tenant/user scope where needed.
- Background jobs must preserve tenant context.
- Audit logs should include tenant/resource context when safe.

## Review Questions

- Can caller change an ID to access another resource?
- Does query filter by owner/tenant?
- Is authorization checked before returning not-found vs forbidden?
- Are bulk operations tenant-scoped?
- Are admin paths audited?

## Failure Modes

- Broken object-level authorization.
- Missing tenant predicate.
- Shared cache leaks data.
- Background job processes wrong tenant.
- Logs expose cross-tenant identifiers.
