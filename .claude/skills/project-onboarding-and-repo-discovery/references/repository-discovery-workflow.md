# Repository Discovery Workflow

## Objective

Discover enough repository context to support safe AI-assisted work without editing files by default.

## Discovery Order

### Phase 1: Boundary and Inventory

Find:

- Repository root.
- Top-level tree.
- Git metadata if relevant.
- Documentation.
- Build files.
- Package manager files.
- CI/CD files.
- Runtime/deployment files.
- Config directories.
- Source and test directories.
- Generated-code directories.

### Phase 2: Source-of-Truth Files

Prioritize:

1. Build files and lockfiles.
2. Test configuration.
3. CI/CD validation.
4. Runtime entrypoints.
5. Configuration loading.
6. Tests and examples.
7. Documentation.

Documentation is useful but may be stale. Confirm important claims through code, config, or tests.

### Phase 3: Entrypoints and Runtime Model

Look for:

- Main classes/functions.
- Server bootstrap.
- CLI commands.
- Worker consumers.
- Schedulers.
- Batch jobs.
- Frontend app roots.
- Infrastructure modules.
- AI pipeline entrypoints.

### Phase 4: Module Boundaries

Identify:

- Independent modules/packages.
- Shared libraries.
- Adapters/infrastructure layer.
- Domain/core layer.
- API layer.
- Generated sources.
- Test utilities.

Avoid imposing Clean Architecture, DDD, MVC, or framework-specific assumptions unless the repo demonstrates them.

### Phase 5: Internal Abstractions

Search usage examples for:

- Internal namespaces.
- Custom annotations/decorators.
- Base classes.
- Factories/builders.
- Dependency injection modules.
- Config readers.
- RPC abstractions.
- Client/server wrappers.
- Logging/metrics/tracing wrappers.
- Test harnesses.

### Phase 6: Validation Discovery

Identify commands from:

- README.
- Build files.
- Package scripts.
- Make targets.
- CI files.
- Docker/compose files.
- Test configs.
- Developer scripts.

Classify commands as:

- Confirmed.
- Candidate.
- Unsafe without approval.
- Unknown.

### Phase 7: Risk Review

Flag:

- Auth/security.
- Secrets.
- Migrations.
- Production configs.
- CI/CD.
- Infrastructure.
- Generated code.
- Dependency upgrades.
- Data deletion/mutation.
- External system writes.

### Phase 8: Report

Produce:

- Compact summary.
- Evidence-backed repo map.
- Validation commands.
- Internal library inventory.
- Unknowns and assumptions.
- Recommended next files.
- Safe next action.
