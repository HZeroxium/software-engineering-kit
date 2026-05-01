# Java Backend Implementation Plan Example

## Task

Implement document processing status query in an existing Java backend.

## Exploration Summary

| Area                      | Evidence                                           | Notes                                        |
| ------------------------- | -------------------------------------------------- | -------------------------------------------- |
| Existing use case pattern | `src/main/java/.../DocumentUploadUseCase.java`     | Use-case classes expose one public operation |
| Repository pattern        | `DocumentJobRepository` usage in tests             | Persistence behind repository abstraction    |
| Tests                     | `src/test/java/.../DocumentUploadUseCaseTest.java` | Unit tests use fake repository               |
| Validation command        | `./gradlew test` from CI                           | Confirmed from workflow                      |

## Affected Files

| File                                  | Change                             |
| ------------------------------------- | ---------------------------------- |
| `DocumentStatusQueryUseCase.java`     | Add query use case                 |
| `DocumentJobRepository.java`          | Add finder if not present          |
| `DocumentStatusResponse.java`         | Add response DTO if repo uses DTOs |
| `DocumentStatusQueryUseCaseTest.java` | Add tests                          |

## Implementation Strategy

1. Add status query use case following existing use-case pattern.
2. Reuse repository abstraction.
3. Enforce caller ownership check before returning status.
4. Return not-found or forbidden using existing error model.
5. Add tests for found, not found, and cross-user access.
6. Run `./gradlew test`.

## Risks

- Cross-user access must be blocked.
- Error semantics must match existing API conventions.
- Do not assume Spring annotations or framework behavior.
