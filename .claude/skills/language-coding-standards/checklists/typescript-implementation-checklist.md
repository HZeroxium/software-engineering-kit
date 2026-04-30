# TypeScript Implementation Checklist

## Context

- [ ] TypeScript config is inspected or uncertainty is stated.
- [ ] Existing project style is inspected.
- [ ] Framework conventions are respected.
- [ ] Public API impact is understood.

## Types

- [ ] Exported APIs have clear types.
- [ ] `any` is avoided unless justified.
- [ ] `unknown` is narrowed at boundaries.
- [ ] Null/undefined handling is explicit.
- [ ] Domain states are modeled clearly.

## Runtime Boundaries

- [ ] External input is validated.
- [ ] API responses are checked before trusted use.
- [ ] Environment/config values are validated.
- [ ] Errors are handled at async boundaries.
- [ ] Unawaited promises are intentional and observed.

## Frontend Awareness

- [ ] Loading state is handled.
- [ ] Error state is handled.
- [ ] Empty state is handled.
- [ ] Accessibility is considered.
- [ ] State ownership is clear.
- [ ] Secrets are not exposed to client bundles.

## Tests and Validation

- [ ] Unit/integration/component tests are considered.
- [ ] Typecheck/lint/build commands are discovered from repo.
- [ ] Regression tests are added for bug fixes.
