# Authorization Checklist

- [ ] Caller identity is established.
- [ ] Action is defined.
- [ ] Resource is defined.
- [ ] Required permission is defined.
- [ ] Object ownership is checked.
- [ ] Tenant boundary is checked.
- [ ] Bulk operations are scoped.
- [ ] Admin bypasses are audited.
- [ ] Background jobs preserve authorization/tenant context where needed.
- [ ] Tests cover allowed and denied access.
- [ ] Cross-user or cross-tenant access test exists where relevant.
