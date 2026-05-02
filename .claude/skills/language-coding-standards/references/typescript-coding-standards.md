---
purpose: TypeScript language-level coding standards for strict typing, runtime boundaries, modules, async behavior, and frontend-aware code
load-when: Working in TypeScript code or reviewing TypeScript-specific typing, runtime validation, module, async, or frontend code-level choices
tier: domain
see-also:
  - error-handling-standards.md
  - dependency-and-library-usage.md
  - naming-and-readability.md
  - immutability-and-state.md
  - concurrency-and-async.md
---

# TypeScript Coding Standards

## Core Principle

Prefer strict, explicit TypeScript with clear module boundaries and runtime validation for external input.

## Typing

- Prefer explicit types for public functions and exported APIs.
- Avoid `any`; use `unknown` at untrusted boundaries and narrow it.
- Preserve strict null/undefined handling according to project config.
- Model domain states with discriminated unions when useful.
- Avoid excessive generic abstraction.
- Keep inferred local types when they improve readability.

## Runtime Validation

TypeScript types do not validate runtime data.

Validate:

- HTTP request payloads.
- API responses from external services.
- Environment/config values.
- Local storage/session data.
- Message/event payloads.
- User input.

Use the project’s existing validation library or pattern. Do not introduce new libraries without approval.

## Null and Undefined

- Distinguish absent, null, empty, and default values.
- Avoid non-null assertions unless the invariant is obvious and safe.
- Prefer early validation or narrowing.
- Avoid optional chains that hide required data errors.

## API Contracts

- Keep request/response types stable.
- Do not expose internal implementation types as external contracts accidentally.
- Model error responses explicitly.
- Consider backward compatibility for exported types.

## Async Error Handling

- Always handle rejected promises at boundaries.
- Avoid unawaited promises unless intentionally detached and observed.
- Use timeouts for external calls when project convention supports it.
- Avoid retrying non-idempotent operations.
- Keep cancellation/abort behavior in mind for UI and network calls.

## Module Boundaries

- Keep modules cohesive.
- Avoid circular dependencies.
- Avoid mixing UI, API client, domain logic, and persistence concerns.
- Export only intended APIs.
- Keep shared utility modules focused.

## React / Frontend Awareness

When working in frontend code:

- Preserve accessibility.
- Handle loading, error, and empty states.
- Avoid unnecessary re-renders.
- Keep state ownership clear.
- Validate external data before rendering important assumptions.
- Avoid leaking secrets to client bundles.

## Testability

- Keep pure logic testable.
- Mock external boundaries, not internal logic.
- Test edge and error cases.
- Add regression tests for bug fixes.
