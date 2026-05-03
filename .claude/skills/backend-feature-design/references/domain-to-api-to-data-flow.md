---
purpose: Core reasoning sequence for translating business capability into domain concepts, API contract, application workflow, and data ownership
load-when: Early design phase — translating feature intent into domain concepts, API contract, or data ownership
tier: foundational
see-also:
  - backend-design-workflow.md
  - transaction-and-consistency-thinking.md
---

# Domain to API to Data Flow

## Purpose

Use this reference to translate feature intent into backend design without prematurely choosing a framework.

## Reasoning Sequence

```text
Business capability
  -> domain concepts and invariants
  -> API/interface contract
  -> application workflow
  -> data ownership and persistence
  -> integration and side effects
  -> validation and observability
```

## Domain Layer Questions

- What business capability is being added or changed?
- What are the core concepts?
- What rules must always hold?
- What states can the entity/workflow enter?
- What transitions are valid?
- What business events exist?

## API / Interface Questions

- Who calls the backend?
- Is this a command, query, event, callback, or internal operation?
- What request fields are required?
- What response fields are stable?
- What errors are expected?
- Is the operation idempotent?
- Is the API backward compatible?

## Application Workflow Questions

- What steps happen in order?
- Which steps require transactionality?
- Which steps can be asynchronous?
- Where do side effects occur?
- What happens on partial failure?
- What is retried, and what is not?

## Data Questions

- What state is read?
- What state is written?
- Who owns this data?
- Which constraints enforce correctness?
- Are indexes required?
- Is a migration required?
- Is caching safe?
- What lifecycle rules apply?

## Example: Java-Oriented But Framework-Agnostic

```text
DocumentUploadCommand
  -> Validate caller and request
  -> Create Document aggregate in PENDING_SCAN state
  -> Persist document metadata
  -> Enqueue scan job after commit
  -> Return document ID and current status
```

Possible Java abstractions:

```text
DocumentUploadUseCase
DocumentRepository
DocumentStoragePort
DocumentScanJobPublisher
DocumentStatus
```

These names are examples only. Follow repository conventions when available.
