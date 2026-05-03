---
purpose: Module boundary design for modular monoliths — ownership, public APIs, and cycle prevention
load-when: Reviewing module boundaries, ownership, or dependency cycles
tier: domain
see-also:
  - dependency-architecture.md
---

# Modular Monolith and Multi-Module Backend

## Purpose

Support strong internal boundaries without prematurely splitting services.

## Good Modular Monolith Traits

- Clear business modules.
- Explicit public APIs between modules.
- Internal implementation hidden.
- Dependency direction enforced.
- Separate tests per module.
- Shared infrastructure kept minimal.

## Multi-Module Questions

- What does each module own?
- Which module can depend on which?
- Which API is public vs internal?
- Are cycles prevented?
- Does module structure match business capability?

## Failure Modes

- Modules are technical layers only.
- Shared module becomes dumping ground.
- All modules access all data.
- No ownership over contracts.
- Circular dependencies.
