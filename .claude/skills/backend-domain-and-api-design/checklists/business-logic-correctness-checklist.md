# Business Logic Correctness Checklist

- [ ] Expected behavior matches requirement.
- [ ] Business rules are enforced.
- [ ] Domain invariants cannot be bypassed.
- [ ] Invalid state transitions are rejected.
- [ ] Edge cases covered.
- [ ] Duplicate/retry behavior handled.
- [ ] Authorization does not change business outcome incorrectly.
- [ ] Persistence constraints protect critical uniqueness.
- [ ] Errors distinguish validation, business, and technical failures.
- [ ] Tests cover success, failure, and edge cases.
- [ ] Background jobs/internal flows cannot bypass rules.
- [ ] Concurrency/race conditions considered where relevant.
