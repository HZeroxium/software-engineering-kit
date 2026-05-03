---
purpose: Multi-step workflow design — durable steps, retry, compensation, stuck-state detection, and failure recovery
load-when: Designing or reviewing multi-step async, event-driven, job, or saga-like workflows
tier: domain
see-also:
  - state-machines.md
---

# Workflow Orchestration

## Purpose

Design multi-step backend workflows that remain correct under failure and retry.

## Workflow Types

- Synchronous request workflow.
- Asynchronous job workflow.
- Event-driven workflow.
- Scheduled/batch workflow.
- Human approval workflow.
- Distributed saga-like workflow.

## Design Questions

- What are the steps?
- Which steps are durable?
- Which steps are retryable?
- Which steps are compensatable?
- What state records progress?
- What observes failures?
- What resumes stuck work?

## Failure Modes

- Workflow state only exists in memory.
- Background job has no idempotency.
- Step failure loses progress.
- No stuck-state detection.
- Retry repeats irreversible side effects.
