---
purpose: Authorization model selection, review questions, decision guide, and common smells
load-when: Task involves authorization design, role/permission model, or access control review
tier: domain
see-also:
  - object-level-and-tenant-access-control.md
---

# Authorization Models

## Purpose

Determine what an authenticated identity can do.

## Models

| Model         | Description                   | Risks                          |
| ------------- | ----------------------------- | ------------------------------ |
| RBAC          | Role-based permissions        | Roles too broad                |
| ABAC          | Attribute/policy-based access | Policy complexity              |
| ReBAC         | Relationship-based access     | Relationship graph correctness |
| ACL           | Resource-specific permissions | Scaling/maintenance            |
| Custom policy | Domain-specific rules         | Hidden logic and inconsistency |

## Questions

- What action is being authorized?
- What resource is being accessed?
- What permission is required?
- Which attributes matter?
- Where is the check enforced?
- Is authorization centralized, local, or mixed?

## Smells

- Authentication but no authorization.
- Route-level check only.
- Object ownership not checked.
- Admin bypass without audit.
- Authorization duplicated inconsistently.

## Decision Guide

| Scenario | Recommended Model |
|----------|-------------------|
| Simple user roles (admin, viewer, editor) with stable set of permissions | RBAC |
| Fine-grained conditions based on attributes (owner, department, time, tier) | ABAC |
| Graph-based ownership (e.g., can edit because member of team that owns resource) | ReBAC |
| Per-resource permission lists for heterogeneous access needs | ACL |
| Complex domain-specific rules mixing multiple factors | Custom policy — document explicitly |

Prefer the simplest model that covers current requirements. Document the chosen model in code or architecture notes. Avoid mixing models without a clear boundary.
