---
purpose: Input injection risks and output exposure risks with review questions and validation
load-when: Task involves input validation, injection risk, or API response exposure review
tier: domain
see-also:
  - external-call-security.md
---

# Input and Output Security

## Input Risks

- Injection.
- SSRF.
- Path traversal.
- Unsafe deserialization.
- File upload abuse.
- Command injection.
- XML/entity expansion.
- Unbounded payloads.
- Malicious URLs.
- Header spoofing.

## Output Risks

- Sensitive data exposure.
- Stack traces.
- Internal IDs.
- Excessive error detail.
- Unsafe redirects.
- Unescaped output.
- Over-broad response fields.

## Review Questions

- Is input validated by allowlist?
- Are URLs restricted?
- Are file paths normalized and sandboxed?
- Are payload sizes bounded?
- Is output minimized?
- Are errors safe?

## Validation

- Negative tests.
- Boundary tests.
- Security review.
- Static analysis where available.
