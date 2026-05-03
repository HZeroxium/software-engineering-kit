---
purpose: When to use async messaging, common forms (queue/pub-sub/event stream), design questions, and failure modes
load-when: Task involves message queues, pub/sub, event streams, webhooks, or scheduled jobs
tier: foundational
see-also:
  - event-contracts.md
  - idempotent-consumers.md
---

# Asynchronous Messaging

## Purpose

Use asynchronous messaging when work can happen later, needs buffering, or should decouple producer and consumer.

## Common Forms

- Queue.
- Pub/sub.
- Event stream.
- Command message.
- Scheduled job.
- Webhook callback.

## Design Questions

- Is the message a command or event?
- Who owns the schema?
- Are duplicates possible?
- Is ordering required?
- How are failures retried?
- Is there dead-letter or poison-message handling?
- How is consumer lag/backlog observed?

## Failure Modes

- Assuming exactly-once delivery.
- Consumer not idempotent.
- Unbounded queue growth.
- Event schema breaks consumers.
- Missing dead-letter handling.
- No replay/recovery process.

## Dead-Letter Queue Design

A dead-letter queue (DLQ) captures messages that cannot be processed after a defined number of retry attempts.

Use when:
- Consumer failures are expected and must not block healthy messages.
- Poison messages (malformed, schema-incompatible, or permanently unprocessable) must be isolated.
- Operational visibility into processing failures is required.

Design considerations:

| Concern | Decision |
| --- | --- |
| Retry limit before DLQ | Define a maximum delivery count; route to DLQ on exhaustion |
| DLQ alerting | Alert when DLQ depth exceeds zero or grows past a threshold |
| Replay process | Define whether replay is manual or automated; test replay before relying on it |
| Poison message handling | Skip (discard), park (DLQ), or manual repair — document the policy |
| DLQ retention | Set a retention window; expired messages cannot be replayed |

Review questions:
- What triggers a message to be sent to the DLQ?
- Who is alerted when the DLQ receives a message?
- Can messages be replayed from the DLQ safely (consumer is idempotent)?
- Is there a process to inspect and manually repair poison messages?
