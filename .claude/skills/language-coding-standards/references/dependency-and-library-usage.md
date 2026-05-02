---
purpose: Cross-language dependency and library usage standards for approval, selection, version discipline, and security review
load-when: Adding, replacing, upgrading, or justifying a dependency or library choice
tier: domain
see-also: []
---

# Dependency and Library Usage

## Default Rule

Do not introduce a new dependency unless it is clearly justified and user-approved.

Prefer existing project dependencies and conventions.

## Before Adding a Library

Check:

- Is similar functionality already available?
- Is standard library enough?
- Is the library actively maintained?
- Is license acceptable?
- Is security posture acceptable?
- Is transitive dependency risk acceptable?
- Is bundle/runtime size acceptable?
- Is API stable?
- Does it work with project runtime version?
- Does the team already use it?

## Good Reasons to Add

- Security-critical implementation should not be hand-rolled.
- Protocol/client is complex and standardized.
- Existing project already uses the library.
- The library significantly reduces tested complexity.
- Maintenance burden is lower than custom implementation.

## Poor Reasons to Add

- Minor convenience.
- One small helper.
- Avoiding simple code.
- Unknown API copied from memory.
- New pattern inconsistent with repo.
- Dependency only helps generated code.

## Version Discipline

- Do not invent versions.
- Inspect dependency files.
- Preserve lockfiles unless dependency change is intentional.
- Avoid broad upgrades without approval.
- Consider compatibility with runtime and framework version.

## Security

- Avoid libraries with known vulnerabilities.
- Avoid abandoned packages for critical paths.
- Do not add packages that execute install scripts or access network unless necessary and approved.
