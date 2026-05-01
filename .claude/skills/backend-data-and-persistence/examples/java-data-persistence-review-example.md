# Java Data/Persistence Review Example

## Scenario

Review a Java backend query that fetches document jobs by `jobId`.

## Finding

The query loads a document job by `jobId` only. In a multi-user or multi-tenant system, this can leak another user’s job status.

## Risk

- **Scope:** Data/persistence and security/trust.
- **Severity:** Blocking if document jobs are user-owned.
- **Failure mode:** Caller changes `jobId` and reads another user’s data.

## Minimal Fix

Use a tenant/user-scoped lookup:

```java
Optional<DocumentJob> findByOwnerAndId(UserId ownerId, DocumentJobId jobId);
```

## Additional Data Considerations

- Add or verify index on `(owner_id, job_id)`.
- Ensure cache key includes `ownerId` or tenant ID.
- Add test for cross-owner access denial.

## Validation

- Unit or integration test for owner-scoped lookup.
- Query/index review.
- Authorization review.
