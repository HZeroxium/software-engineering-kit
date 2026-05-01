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
