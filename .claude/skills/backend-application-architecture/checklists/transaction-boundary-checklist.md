# Transaction Boundary Checklist

- [ ] Atomic state changes identified.
- [ ] Non-atomic side effects identified.
- [ ] External calls inside transactions avoided or justified.
- [ ] Critical uniqueness protected by constraints.
- [ ] Concurrency/race conditions considered.
- [ ] Retry behavior defined.
- [ ] Failure after commit handled.
- [ ] Message/event publishing reliability considered.
- [ ] Transaction semantics confirmed from repo evidence.
- [ ] Tests cover success, failure, and concurrency where needed.
