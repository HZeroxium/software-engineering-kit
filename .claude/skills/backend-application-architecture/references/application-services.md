---
purpose: Responsibilities and anti-patterns for application services; god service detection
load-when: Designing or reviewing application service boundaries
tier: domain
see-also:
  - use-case-orchestration.md
---

# Application Services

## Purpose

Application services coordinate use cases. They should not become god services.

## Good Responsibilities

- Orchestrating a single use case.
- Coordinating domain objects and ports.
- Managing transaction boundaries when repo conventions support it.
- Calling external adapters through abstractions.
- Handling application-level errors.
- Returning use-case results.

## Poor Responsibilities

- Owning all business rules.
- Building SQL directly when domain/data boundaries say otherwise.
- Managing transport-specific details.
- Formatting API responses.
- Holding unrelated workflows.
- Constructing all infrastructure directly.

## Java-Oriented Shape

```java
public final class SubmitDocumentUseCase {
    private final DocumentRepository documents;
    private final DocumentJobPublisher publisher;

    public SubmitDocumentResult execute(SubmitDocumentCommand command) {
        // Orchestration only; details depend on repo conventions.
        return null;
    }
}
```

Use existing project conventions first.
