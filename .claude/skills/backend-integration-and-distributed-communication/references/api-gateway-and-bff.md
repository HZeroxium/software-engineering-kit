---
purpose: API gateway and BFF pattern scope, acceptable vs risky gateway responsibilities, and review questions for cross-cutting boundaries
load-when: Integration involves an API gateway, BFF layer, protocol translation, or cross-cutting client-facing boundary
tier: scenario
see-also: []
---

# API Gateway and BFF

## Purpose

Use gateway or BFF patterns to shape client access without letting the gateway become a distributed monolith.

## Gateway Responsibilities

Acceptable:

- Routing.
- Authentication delegation.
- Rate limiting.
- Request shaping.
- Response aggregation when lightweight.
- Protocol translation.
- Cross-cutting policy enforcement.

Risky:

- Owning core business rules.
- Holding workflow state.
- Performing heavy orchestration.
- Hiding downstream errors.
- Coupling many services into one critical path.

## Review Questions

- Is logic client-specific or business-core?
- Does aggregation increase latency/failure surface?
- Are downstream timeouts isolated?
- Are errors mapped safely?
- Is observability preserved across boundaries?
