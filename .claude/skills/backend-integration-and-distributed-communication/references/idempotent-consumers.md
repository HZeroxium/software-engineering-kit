---
purpose: Consumer idempotency rules, deduplication key design, failure modes for duplicate message delivery
load-when: Consumer may receive duplicate messages, or retry behavior may cause repeated side effects
tier: domain
see-also:
  - outbox-inbox-patterns.md
---

# Idempotent Consumers

## Purpose

Handle duplicate message delivery safely.

## Consumer Idempotency Rules

- Identify message uniquely.
- Store processed message ID or natural dedup key.
- Make side effects repeat-safe.
- Handle crash after partial processing.
- Return success for already processed duplicate when appropriate.

## Design Questions

- What uniquely identifies the message?
- Is deduplication global, tenant-scoped, or resource-scoped?
- How long is dedup state retained?
- What side effects happen?
- What happens if processing fails after one side effect?

## Failure Modes

- Duplicate DB writes.
- Duplicate notifications.
- Double external provider call.
- Message acknowledged before durable state.
- Dedup key excludes tenant/resource.
