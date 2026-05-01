# Java Domain/API Design Example

## Feature

Design an API for submitting document processing jobs.

## Domain Concepts

| Concept                 | Type         | Responsibility               |
| ----------------------- | ------------ | ---------------------------- |
| `DocumentJob`           | Entity       | Tracks processing lifecycle  |
| `JobStatus`             | Value/Enum   | Represents valid states      |
| `DocumentSubmitted`     | Domain event | Signals durable job creation |
| `SubmitDocumentCommand` | Command      | Caller intent                |

## Business Rules

- A job starts in `PENDING`.
- A `COMPLETED` or `FAILED` job is terminal.
- A caller can only query jobs they own.
- A duplicate submission with the same idempotency key returns the original job.

## API Sketch

```text
POST /document-jobs
Request:
- idempotencyKey
- documentReference
- metadata

Response:
- jobId
- status
```

## Error Model

| Error                                            | Retryable? | Client Action                   |
| ------------------------------------------------ | ---------: | ------------------------------- |
| Invalid document reference                       |         No | Fix request                     |
| Duplicate idempotency key with different payload |         No | Use original payload or new key |
| Processing queue unavailable                     |        Yes | Retry with same key             |
| Unauthorized owner                               |         No | Re-authenticate or stop         |

## Tests

- Submit valid document creates `PENDING` job.
- Duplicate submit returns original job.
- Duplicate submit with different payload returns conflict.
- Invalid state transition is rejected.
- Cross-user query is denied.
