---
purpose: Secrets handling rules, review questions, and common smells
load-when: Task involves credentials, API keys, tokens, certificates, or sensitive config
tier: domain
see-also: []
---

# Secrets Management

## Purpose

Protect credentials, tokens, certificates, API keys, signing keys, and private config.

## Rules

- Do not print secrets.
- Do not commit secrets.
- Do not put secrets in prompts, logs, traces, metrics, or errors.
- Separate secrets from normal config.
- Prefer managed secret stores where organization conventions support them.
- Rotate and audit secret access.

## Review Questions

- Is this value a secret?
- Where is it stored?
- Who can read it?
- Is it logged?
- Is it sent externally?
- Can it be rotated?
- Is access audited?

## Smells

- Secrets in source code.
- Secrets in `.env` committed to repo.
- Secrets in CI logs.
- Secrets in exception messages.
- Long-lived credentials without rotation.
