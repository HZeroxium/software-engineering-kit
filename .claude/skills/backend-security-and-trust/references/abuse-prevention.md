# Abuse Prevention

## Purpose

Design backend systems to resist misuse, overload, fraud, scraping, spam, and automated abuse.

## Controls

- Rate limiting.
- Quotas.
- Bot detection where appropriate.
- Replay protection.
- Idempotency.
- Captcha or challenge for public endpoints where appropriate.
- Abuse monitoring.
- Account lockout protections.
- Provider cost limits.

## Questions

- Can anonymous callers abuse this endpoint?
- Can authenticated users create excessive work?
- Can retries amplify cost?
- Are expensive operations bounded?
- Are public APIs rate-limited?
- Are AI/model calls cost-limited?

## Failure Modes

- Cost blowup.
- Resource exhaustion.
- Spam/notification abuse.
- Credential stuffing.
- Replay attack.
- Queue overload.
