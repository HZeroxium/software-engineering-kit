# Idempotency and Retry Safety

## Purpose

Prevent duplicate side effects when clients, workers, or message brokers retry operations.

## Use Idempotency When

- Client may timeout and retry.
- Payment/order/job/notification side effects exist.
- Message delivery is at-least-once.
- External provider call may succeed but response is lost.
- Operation is not naturally idempotent.

## Design Questions

- What key identifies a duplicate?
- Who generates the key?
- What is the deduplication scope?
- What is the deduplication window?
- Is the original result stored?
- What response is returned for duplicate requests?
- What happens under concurrent duplicates?

## Storage Patterns

- Unique constraint on natural key.
- Idempotency table.
- Inbox table for consumed messages.
- Outbox table for reliable publishing.
- Provider-side idempotency key.

## Failure Modes

- Duplicate resource creation.
- Double payment.
- Duplicate email/notification.
- Replayed webhook accepted.
- Concurrent requests race past app-level check.
- Retry turns transient failure into data corruption.
