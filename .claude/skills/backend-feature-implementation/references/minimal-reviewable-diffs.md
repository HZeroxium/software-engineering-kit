---
purpose: Principles and rules for keeping backend changes small, focused, and independently reviewable
load-when: Planning or reviewing edit scope; deciding whether to split a change; noticing the planned change is growing large
tier: domain
see-also:
  - backend-implementation-workflow.md
---

# Minimal Reviewable Diffs

## Principle

Prefer small, focused backend changes that reviewers can validate against the design and tests.

## Good Diff Properties

- One clear behavior change.
- Minimal unrelated formatting.
- Tests close to changed behavior.
- Existing conventions preserved.
- Public contracts changed only when explicit.
- Risky changes separated when possible.
- Generated code handled through generator workflow.
- Validation evidence included.

## Split Changes When

- Feature logic and broad refactor are mixed.
- Migration and application behavior are mixed.
- Dependency upgrade and feature change are mixed.
- Security-sensitive changes are mixed with non-security cleanup.
- Generated code obscures source changes.
- Observability changes are large enough to review independently.

## Avoid

- Drive-by rewrites.
- Renaming unrelated files.
- Formatting unrelated areas.
- Replacing internal abstractions without evidence.
- Changing public errors casually.
- Changing transaction behavior without tests.
- Updating dependencies “because available”.
