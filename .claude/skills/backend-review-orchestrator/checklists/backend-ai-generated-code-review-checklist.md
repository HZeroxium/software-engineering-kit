# Backend AI-Generated Code Review Checklist

## AI-Specific Risks

- [ ] Invented APIs.
- [ ] Invented internal library behavior.
- [ ] Framework assumptions not supported by repo evidence.
- [ ] Missing authorization.
- [ ] Missing object-level access control.
- [ ] Missing transaction safety.
- [ ] Missing idempotency.
- [ ] Missing error handling.
- [ ] Missing tests.
- [ ] Over-broad rewrite.
- [ ] Style inconsistent with repo.
- [ ] Unvalidated commands or dependencies.
- [ ] Secrets or sensitive data exposed.
- [ ] Generated code modified manually.
- [ ] Public contract changed unintentionally.

## Required Review Behavior

- [ ] Compare against repository patterns.
- [ ] Check tests and build config.
- [ ] Verify internal library usage from examples.
- [ ] Ask for missing context instead of guessing.
- [ ] Recommend minimal fixes.
- [ ] Require validation evidence.
