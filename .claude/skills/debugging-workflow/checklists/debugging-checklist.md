---
purpose: End-to-end debugging completeness check
load-when: Before summarizing debugging work, when the task is broad, or when audit completeness matters
---

# Debugging Checklist

## Problem Definition

- [ ] Expected behavior is clear.
- [ ] Actual behavior is clear.
- [ ] Error message is captured.
- [ ] Reproduction steps are captured.
- [ ] Scope is known.
- [ ] Impact is known.

## Evidence

- [ ] Stack trace inspected.
- [ ] Logs inspected.
- [ ] Failing test output inspected.
- [ ] CI output inspected if relevant.
- [ ] Recent changes inspected.
- [ ] Relevant files inspected.
- [ ] Configs inspected.
- [ ] Metrics/traces inspected if available.

## Reasoning

- [ ] Facts are separated from assumptions.
- [ ] Hypotheses are ranked.
- [ ] Experiments are defined.
- [ ] Root cause is not claimed without evidence.
- [ ] Alternative hypotheses are considered.

## Safety

- [ ] No secrets exposed.
- [ ] No production mutation without approval.
- [ ] No destructive command without approval.
- [ ] High-risk changes are escalated.
- [ ] Sensitive logs are redacted.

## Fix

- [ ] Fix targets root cause.
- [ ] Fix is minimal.
- [ ] Regression test is planned.
- [ ] Validation command is discovered from repo.
- [ ] Residual risks are documented.
