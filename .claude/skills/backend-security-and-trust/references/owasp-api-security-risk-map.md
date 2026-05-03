---
purpose: OWASP API Security top-10 risk taxonomy and backend review questions
load-when: Starting any backend security review — load first for risk vocabulary and mapping
tier: foundational
see-also:
  - authorization-models.md
  - authentication-and-service-identity.md
  - input-output-security.md
  - secrets-management.md
  - abuse-prevention.md
  - audit-logging.md
---

# OWASP API Security Risk Map

## Purpose

Use this map to guide backend API security review. Confirm current OWASP details from official sources when needed.

## Risk Themes

- Broken object-level authorization.
- Broken authentication.
- Broken object property-level authorization.
- Unrestricted resource consumption.
- Broken function-level authorization.
- Unrestricted access to sensitive business flows.
- Server-side request forgery.
- Security misconfiguration.
- Improper inventory management.
- Unsafe API consumption.

## Practical Backend Mapping

| Risk Theme                   | Backend Review Question                                      |
| ---------------------------- | ------------------------------------------------------------ |
| Object-level authorization   | Can caller access object by changing ID?                     |
| Authentication               | Is caller identity verified robustly?                        |
| Property-level authorization | Are sensitive fields over-exposed or writable?               |
| Resource consumption         | Are limits, pagination, quotas, and payload bounds enforced? |
| Function-level authorization | Can caller invoke privileged action?                         |
| Sensitive business flow      | Can normal flow be automated or abused?                      |
| SSRF                         | Can caller control backend URL fetches?                      |
| Misconfiguration             | Are debug/admin/security settings safe?                      |
| Inventory                    | Are old APIs still exposed?                                  |
| Unsafe consumption           | Are external API responses validated?                        |
