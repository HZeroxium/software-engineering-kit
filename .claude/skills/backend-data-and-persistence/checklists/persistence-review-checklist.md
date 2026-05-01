# Persistence Review Checklist

- [ ] Query includes required tenant/user filters.
- [ ] Query result size is bounded.
- [ ] Sorting is deterministic.
- [ ] Index supports filters/sorts.
- [ ] Writes are transactional where required.
- [ ] Unique constraints protect critical duplicates.
- [ ] Concurrency/race conditions considered.
- [ ] Repository behavior follows repo conventions.
- [ ] No sensitive data stored unnecessarily.
- [ ] Tests cover persistence behavior.
