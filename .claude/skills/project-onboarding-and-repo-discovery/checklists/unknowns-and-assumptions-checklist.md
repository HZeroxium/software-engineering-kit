# Unknowns and Assumptions Checklist

## Classification Rules

Use these labels:

- **Confirmed:** Direct evidence exists in code, config, tests, CI, or build files.
- **Likely:** Multiple signals agree, but direct confirmation is incomplete.
- **Assumption:** Plausible interpretation with weak evidence.
- **Unknown:** Not enough evidence.

## Common Unknowns to Track

- [ ] Project purpose.
- [ ] Active owner.
- [ ] Canonical build command.
- [ ] Canonical test command.
- [ ] Required local dependencies.
- [ ] Runtime entrypoint.
- [ ] Deployment target.
- [ ] Environment variables.
- [ ] Secret management.
- [ ] Internal library behavior.
- [ ] Generated-code policy.
- [ ] Migration policy.
- [ ] Safe validation command.
- [ ] CI/CD ownership.
- [ ] Production configuration handling.
- [ ] Test data sensitivity.
- [ ] External system side effects.

## Assumption Quality Bar

An assumption is acceptable only when:

- It is clearly labeled.
- Evidence is described.
- Impact is explained.
- A validation path is provided.

## Output Pattern

Use:

- **Unknown:** `<thing>`
- **Why it matters:** `<risk or decision affected>`
- **Evidence checked:** `<files/searches>`
- **How to resolve:** `<next file/question/command>`
