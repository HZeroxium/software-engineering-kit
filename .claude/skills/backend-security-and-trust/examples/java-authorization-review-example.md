# Java Authorization Review Example

## Scenario

A Java backend method returns document processing status by `jobId`.

## Risk

The method loads by `jobId` only and returns status. If `jobId` is caller-controlled, a user may access another user’s job.

## Finding

### Blocking — Missing Object-Level Authorization

- **Scope:** Security/trust and data/persistence.
- **Failure mode:** Cross-user data exposure.
- **Minimal fix:** Query by both actor/owner and job ID, or verify ownership before returning.
- **Validation:** Add denied-access test for another user’s job.

## Safer Shape

```java
public DocumentJobStatus getStatus(UserId actorId, DocumentJobId jobId) {
    DocumentJob job = jobs.findForOwner(actorId, jobId)
        .orElseThrow(() -> new NotFoundException("Document job not found"));

    return job.status();
}
```

## Notes

- Use existing repository error conventions.
- Decide whether unauthorized resources return `403` or hidden `404` based on API policy.
- Audit repeated denied access if this is security-relevant.
