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
