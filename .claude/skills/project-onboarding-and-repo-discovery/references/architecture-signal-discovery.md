---
purpose: Evidence-based signals for inferring module structure, dependency flow, runtime model, and integration model without hallucinating framework or pattern assumptions
load-when: Analyzing module structure, dependency direction, runtime model, or integration model
tier: domain
see-also:
  - internal-library-analysis.md
---

# Architecture Signal Discovery

## Objective

Infer architecture from repository evidence while avoiding framework or pattern hallucination.

## High-Signal Architecture Evidence

Prefer:

- Entrypoint code.
- Module boundaries.
- Dependency direction.
- Tests and fixtures.
- Build modules.
- API definitions.
- Config loading.
- Internal abstractions.
- Runtime wiring.
- CI validation.
- Deployment files.

Use docs as supporting evidence, not sole authority.

## Signals to Capture

### Module Structure

- Monolith, modular monolith, microservices, library, CLI, worker, frontend, infrastructure, AI pipeline, mixed.
- Multi-module build.
- Shared/common modules.
- App vs domain vs infrastructure separation.
- Generated sources.

### Dependency Flow

- Which modules depend on which.
- Whether domain code depends on infrastructure.
- Which modules expose APIs.
- Which modules are adapters.
- Which modules own runtime bootstrap.

### Runtime Model

- Server.
- CLI.
- Worker.
- Scheduler.
- Batch job.
- Library.
- Frontend app.
- AI pipeline/evaluator.
- Infrastructure-only repo.

### Integration Model

- HTTP.
- RPC.
- Messaging.
- Database.
- Cache.
- File storage.
- External APIs.
- Internal services.

### Operational Model

- Config.
- Logs.
- Metrics.
- Tracing.
- Health checks.
- Deployment artifacts.
- CI/CD validation.

## Output Format

For each architecture claim:

- State classification: Confirmed, Likely, Assumption, Unknown.
- Provide evidence.
- Explain implication for future changes.
- Highlight risk.

## Anti-Patterns

Avoid:

- “This is Spring Boot” because Java files exist.
- “This is Clean Architecture” because directories are named domain/application.
- “This uses dependency injection” because constructors exist.
- “This is microservices” because Docker/Kubernetes files exist.
- “This API is REST” because HTTP libraries exist.
- “This generated code can be edited” without generator evidence.
