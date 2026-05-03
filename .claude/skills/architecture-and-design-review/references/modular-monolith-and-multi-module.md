---
purpose: Modular monolith boundaries (package, domain, API, persistence, build, team) and multi-module Java conventions
load-when: Reviewing internal module structure of a single-deployment application or evaluating service extraction readiness
tier: scenario
see-also:
  - layered-architecture.md
  - evolutionary-architecture.md
---

# Modular Monolith and Multi-Module Codebases

## Intent

Keep deployment simple while enforcing clear internal boundaries.

A modular monolith can be a strong default before microservices when service boundaries are still evolving.

## Good Fit

Use when:

- One deployable unit is acceptable.
- Team wants strong module boundaries.
- Domain boundaries are emerging.
- Shared transactions are useful.
- Operational simplicity matters.
- Future service extraction may be possible.

## Boundary Types

- Package/module boundary.
- Domain boundary.
- API boundary.
- Persistence boundary.
- Build module boundary.
- Team ownership boundary.

## Review Questions

- Does each module have a clear responsibility?
- Are dependencies acyclic?
- Is internal implementation hidden?
- Are public module APIs explicit?
- Does one module directly modify another module’s data?
- Are domain concepts duplicated or shared intentionally?
- Can modules be tested independently?
- Are build dependencies minimal?
- Would service extraction be possible if later needed?

## Multi-Module Java Notes

- Avoid circular dependencies.
- Keep shared/common modules small.
- Avoid dumping unrelated utilities into common.
- Prefer explicit public APIs between modules.
- Keep persistence ownership clear.
- Avoid cross-module entity mutation.
- Keep test fixtures organized by module.
