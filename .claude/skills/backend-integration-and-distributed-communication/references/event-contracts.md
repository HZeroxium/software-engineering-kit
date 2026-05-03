---
purpose: Event design rules, backward/forward compatibility, schema registry guidance, and webhook contract safety
load-when: Designing or reviewing event schemas, event naming, schema versioning, or webhook payload contracts
tier: domain
see-also: []
---

# Event Contracts

## Purpose

Keep event contracts stable and safe for distributed consumers.

## Event Design Rules

- Name events as facts, not commands.
- Include stable identifiers.
- Include occurred-at timestamp.
- Include producer/schema version where applicable.
- Minimize sensitive data.
- Make optional fields truly optional.
- Avoid leaking internal database shape.
- Document ordering and duplicate expectations.

## Compatibility

Usually compatible:

- Add optional field.
- Add new event type consumers can ignore.

Potentially breaking:

- Remove field.
- Rename field.
- Change field meaning.
- Change identifier semantics.
- Add required field.
- Change ordering assumptions.

## Validation

- Producer contract test.
- Consumer contract test.
- Schema compatibility check.
- Replay test if supported.

## Schema Registry

Use a schema registry when event schemas are shared across teams or services and backward/forward compatibility must be enforced at publish time.

Common implementations: Confluent Schema Registry, AWS Glue Schema Registry, Apicurio.

Compatibility modes:

| Mode | Allows | Breaks on |
| --- | --- | --- |
| BACKWARD | New schema reads old data | Removing or renaming required fields |
| FORWARD | Old schema reads new data | Adding required fields without defaults |
| FULL | Both backward and forward | Either of the above |
| NONE | No check | Nothing — highest risk |

Default recommendation: BACKWARD compatibility for most event-driven systems. Old consumers can continue reading new events while they migrate.

Schema evolution rules:
- Add optional field with a default value → safe under BACKWARD.
- Remove a field → breaking for consumers that depend on it; requires consumer migration first.
- Rename a field → treat as remove + add; always breaking.
- Change field type → breaking in all modes.

## Webhook Contract Safety

Webhooks are HTTP callbacks triggered by external providers. Treat incoming webhook payloads as untrusted until verified.

**Signature verification:**
- Verify HMAC-SHA256 (or provider-specified algorithm) of the raw request body using the shared secret before processing.
- Do not deserialize before verification.
- Reject requests with missing or invalid signatures with HTTP 401.

**Replay protection:**
- Check the delivery timestamp header (if provided) against a tolerance window (e.g., ±5 minutes).
- Check a delivery ID or nonce against a short-term deduplication store.
- Reject requests outside the tolerance window.

**Idempotency:**
- Webhook handlers must be idempotent — external providers retry on non-2xx responses.
- Use the delivery ID as an idempotency key.

**Failure behavior:**
- Return HTTP 200 quickly to acknowledge receipt; process asynchronously if work is expensive.
- Do not expose internal error details in the response body.
- Track failed deliveries via DLQ or retry table for reconciliation.
