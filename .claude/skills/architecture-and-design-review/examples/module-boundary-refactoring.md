# Example: Module Boundary Refactoring

**Scenario:** A layered Spring Boot monolith's `user` package has grown to own account management, notification preferences, and audit logging alongside core user identity. `UserService` has 18 methods. `UserController` contains validation logic and constructs domain objects directly.

**Skill output type:** `mixed` (analysis + recommendation + spec + summary)

---

## Problem Framing

**Goal:** Reduce `UserService` complexity and stop controller-layer SRP violations before adding a new `preferences` feature.

**Scope:** `user` package only. No service extraction. No new frameworks.

**Non-goals:** Moving to microservices, changing the REST API shape, or altering the database schema.

**Constraints:** Single deployable unit. Team of 3. No dedicated DBA. Shared `users` table owned by this module.

---

## Confirmed Facts

- `UserController` constructs `User` domain objects and contains field validation logic.
- `UserService` owns: identity (create/update/deactivate), password management, notification preference reads/writes, and audit trail writes.
- `UserRepository` is accessed directly from `UserController` in 2 methods for performance shortcuts.
- No package-level API boundary exists — all classes are public.
- Transaction boundary is currently `@Transactional` on `UserService` methods, including notification writes.

---

## Assumptions

| Assumption | Why it matters | How to verify |
|------------|---------------|---------------|
| Notification preferences have different change frequency than identity | Affects whether splitting is worth the cost | Check git log frequency per method group |
| Audit writes do not require same transaction as identity changes | Affects whether outbox or async is safe | Review invariants with team |
| REST API consumers are internal only | Affects compatibility risk of boundary changes | Check API consumers |

---

## Design Options

### Option A: Sub-package split within `user` (recommended)

Extract responsibility groups into sub-packages with explicit public APIs:

```
user/
  identity/         UserIdentityService, UserIdentityRepository
  preferences/      UserPreferencesService, UserPreferencesRepository
  audit/            UserAuditService (async or synchronous)
  api/              UserController (thin), UserRequestDto, UserResponseDto
  domain/           User (domain object, package-private constructors)
```

- `UserController` depends only on `identity/` and `preferences/` services.
- `domain/User` is constructed only inside `identity/`.
- No cross-sub-package repository access.
- Transactions remain scoped within each sub-package service.

**Pros:** Low migration risk. No API change. No new dependencies. Testable sub-units. Reversible.

**Cons:** Still one deployable unit. Does not solve if audit needs different scaling later.

**Best when:** Boundaries are still evolving. Team prefers one deployment. Future service extraction is possible but not imminent.

---

### Option B: Move validation into a dedicated `UserValidator` + keep flat structure

Extract all validation logic from controller into a `UserValidator` component. Keep `UserService` flat but enforce no direct repository access from controller.

**Pros:** Minimal change surface. Fast to implement.

**Cons:** Does not address `UserService` size. Does not create meaningful module boundaries. SRP still violated at service level.

**Best when:** Constraints are very tight, timeline is very short, and future refactoring is planned.

---

## Comparison

| Criterion | Option A | Option B |
|-----------|----------|----------|
| Reduces `UserService` size | Yes | No |
| Enforces dependency direction | Yes | Partially |
| Testability | High | Medium |
| Migration effort | Medium | Low |
| Reversibility | High | High |
| Future service extraction readiness | High | Low |

---

## Recommended Design

**Option A** — sub-package split.

**Dependency direction:**

```text
api/ → identity/, preferences/
identity/ → domain/, audit/
preferences/ → domain/
audit/ → domain/
domain/ → (no outward dependencies)
```

**Module boundary rules:**
- `domain/User` constructor is package-private. Only `identity/` can construct `User`.
- Repository interfaces are package-private within each sub-package.
- `api/` DTOs do not leak into `domain/` or sub-package internals.
- `UserController` has no `@Autowired` repositories.

**Transaction model:** Each sub-package service owns its transaction boundary. Audit writes may be extracted to a separate transaction or async listener when correctness allows.

---

## Risks and Failure Modes

- Circular dependency if `identity/` imports from `preferences/` — prevent with dependency check in review.
- Audit writes currently inside identity transactions — decouple carefully, verify invariants before splitting.
- Test fixtures that construct `User` directly will break when constructor becomes package-private — update fixtures in the same PR.

---

## Testing and Validation Strategy

- Unit tests for each sub-package service with mocked dependencies.
- Integration test for `identity/` covering `UserIdentityService` → `UserIdentityRepository` → database.
- Contract test for `UserController` verifying API response shape is unchanged.
- Confirm no cross-sub-package repository access with a static analysis check or code review gate.

---

## Architecture Decision Note

**Title:** Split `user` package into sub-packages with explicit boundaries

**Status:** Proposed

**Decision:** Extract `identity`, `preferences`, `audit`, and `api` sub-packages. Enforce dependency direction via package-private constructors and repository interfaces.

**Rationale:** `UserService` violates SRP, `UserController` constructs domain objects, and direct repository access from controllers creates unmaintainable shortcuts. Sub-package split is the lowest-risk boundary enforcement without microservices overhead.

**Consequences:**
- Positive: Easier to test, change, and reason about each responsibility group independently.
- Negative: Medium migration effort — all tests referencing `User` constructors must be updated.
- Neutral: No API change, no new dependencies, no deployment topology change.

**Rollback:** Sub-package split is fully reversible — classes can be merged back if boundaries prove unhelpful.
