# Harness Engineering and Validation

## Goal

Use deterministic validation to increase confidence in changes.

Do not trust generated code, plans, or docs without checking them against repository evidence and available verification commands.

## Discover Verification Commands

Discover canonical build, test, lint, typecheck, and static-analysis commands from repository sources such as:

- README
- CONTRIBUTING docs
- Developer docs
- Package manager files
- Maven files
- Gradle files
- Makefile
- Taskfile
- Justfile
- npm/yarn/pnpm/bun scripts
- Python project files
- CI configs
- Docker files
- Docker Compose files
- Scripts directory
- Existing documentation
- Existing agent instructions

Do not invent verification commands.

If commands cannot be discovered:

- State uncertainty.
- Propose likely commands only as assumptions.
- Prefer asking the user or inspecting more repo context.
- Do not present assumed commands as confirmed.

## Validation Strategy

Choose the narrowest useful validation first:

- Run or recommend targeted tests for changed code.
- Run type checking or compilation for affected modules.
- Run lint/static analysis when available.
- Run broader checks only when targeted checks pass or when the change has broad impact.

For high-risk changes, include manual review in the validation plan.

## Exit Criteria

A change is ready to summarize when:

- Relevant tests pass.
- Build, typecheck, lint, or static analysis pass when available.
- Public API or behavior changes are documented.
- Observability is considered for behavior or failure-mode changes.
- Security-sensitive changes receive manual review.
- Diff is minimal and reviewable.
- Residual risks are documented.
- Tests not run are explicitly listed with reasons.

## Fix Loop

When a check fails:

1. Inspect the failure.
2. Determine whether the test is wrong, code is wrong, or environment is wrong.
3. Apply the minimal fix.
4. Rerun the relevant check.
5. Repeat only while the failure cause is clear and the risk remains acceptable.
6. Stop and escalate if the failure cause is unclear or risk is high.

Do not blindly change code to satisfy tests without understanding the behavior.

## Evidence Discipline

When validating:

- Prefer exact command output summaries over vague claims.
- State pass/fail clearly.
- Include what was run and from where.
- Include what was not run.
- Mention environment limitations.
- Avoid claiming CI parity unless the command is clearly the CI command.

## Behavior Changes

For behavior changes, consider validation through:

- Unit tests
- Integration tests
- API contract tests
- Regression tests
- Manual reproduction
- Logs
- Metrics
- Feature flags
- Rollback plan
- Documentation update

## Observability Validation

When a change affects runtime behavior or failure modes, consider:

- Logs for important state transitions and errors
- Metrics for throughput, latency, error rate, saturation, or business events
- Traces for distributed flows
- Alerting implications
- Dashboard impact
- Safe redaction of sensitive data

Do not add noisy logs or high-cardinality metrics without justification.

## Security Validation

For security-sensitive changes, consider:

- Authorization tests
- Authentication tests
- Negative tests
- Input validation tests
- Secret leakage checks
- Dependency vulnerability review
- Manual security review
- Threat model update when needed

## Documentation Validation

For documentation changes:

- Ground claims in code, configs, tests, scripts, or current behavior.
- Verify commands before documenting them.
- Mark assumptions explicitly.
- Avoid idealized architecture that does not match the repository.
