# Saga and Compensation

## Purpose

Coordinate distributed business workflows without assuming distributed transactions.

## Saga

A saga is a sequence of local transactions with compensating actions for failures.

## Use When

- Workflow spans multiple services/resources.
- Atomic distributed transaction is unavailable or undesirable.
- Business can tolerate intermediate states.
- Compensation is meaningful.

## Questions

- What are the local steps?
- What state records progress?
- What compensation exists for each completed step?
- What failures are non-compensatable?
- Who owns orchestration?
- How are retries and manual repair handled?

## Failure Modes

- Compensation missing.
- Workflow state only in memory.
- Duplicate compensation.
- User sees confusing intermediate state.
- No reconciliation process.
