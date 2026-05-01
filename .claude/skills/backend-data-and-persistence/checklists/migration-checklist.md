# Migration Checklist

- [ ] Migration is backward compatible.
- [ ] Old app works with new schema.
- [ ] New app works during rollout.
- [ ] Destructive changes delayed until safe.
- [ ] Backfill plan exists if needed.
- [ ] Backfill is rate-limited if large.
- [ ] Index creation production impact checked.
- [ ] Rollback plan exists.
- [ ] Migration tested locally/CI if possible.
- [ ] Monitoring plan exists.
- [ ] Human approval obtained for production-impacting migration.
