---
purpose: Security patterns for outbound HTTP calls, webhook consumption, and third-party API trust
load-when: Task involves outbound calls, SSRF risk, webhook handlers, or third-party API integration
tier: scenario
see-also:
  - input-output-security.md
---

# External Call Security

## Purpose

Prevent backend services from being weaponized through SSRF, webhook replay abuse, or unsafe third-party API consumption.

## SSRF

- Validate and allowlist target URLs before making outbound calls.
- Block private IP ranges, localhost, and cloud metadata endpoints (e.g., `169.254.169.254`).
- Do not pass caller-controlled URLs directly to backend HTTP clients.
- Prefer DNS-rebinding-safe HTTP clients when available.
- Log all outbound call targets for audit and anomaly detection.

## Webhook Consumption

- Verify webhook signatures (HMAC-SHA256 or provider-specific signing) before any processing.
- Reject unverified payloads unconditionally — do not process first and verify later.
- Treat all webhook payload fields as untrusted input (validate before use).
- Use idempotency keys to prevent duplicate processing from replayed or retried deliveries.
- Return `200` quickly; process asynchronously if the handler is slow.

## Third-Party API Trust

- Validate response schema and field types before using response values.
- Do not forward raw external API responses to callers without sanitization.
- Limit credential scope sent to external providers — use the minimum required.
- Bound external API cost — configure quotas, timeouts, and circuit breakers.
- Handle external failures without leaking internal system details in error responses.
- Treat third-party response data as untrusted input: validate, type-check, and sanitize.

## Review Questions

- Who controls the target URL — the backend system or the caller?
- Is SSRF possible via user-controlled input (URL, hostname, redirect)?
- Are webhooks signature-verified before any business logic executes?
- Is the external API response validated before use?
- Are credentials scoped to the minimum required scope?
- Is the external call observable — logs, metrics, and alerts on failure or anomaly?

## Failure Modes

- SSRF via user-controlled URL targeting internal services or cloud metadata endpoints.
- Replay attack via unverified or replayed webhook payload.
- Data injection via malicious or malformed external API response.
- Credential over-sharing with third-party providers.
- Cost blowup from unguarded or unbounded external API calls.
- Sensitive data leakage in outbound request bodies or headers.
