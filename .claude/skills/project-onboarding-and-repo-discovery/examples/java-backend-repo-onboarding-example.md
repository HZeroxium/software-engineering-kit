# Java Backend Repository Onboarding Example

## Summary

- **Repository:** `example-user-service`
- **Primary purpose:** Likely user profile backend service.
- **Primary language:** Java.
- **Frameworks confirmed:** No public framework confirmed from the initial scan.
- **Internal libraries detected:** Yes.
- **Read-only status:** No files modified.

## Confirmed Facts

- The repository uses Gradle because `settings.gradle`, `build.gradle`, and `gradlew` are present.
- Java production code is under `src/main/java`.
- Java tests are under `src/test/java`.
- Runtime resources are under `src/main/resources`.
- CI uses `./gradlew check` in `.github/workflows/ci.yml`.
- There is a main class at `src/main/java/com/acme/user/Main.java`.
- Internal packages under `com.acme.platform.*` are used for configuration, RPC server bootstrap, and metrics.

## Likely Interpretation

This appears to be a Java backend service with an internal platform runtime wrapper. The service likely exposes RPC endpoints through internal abstractions rather than raw framework APIs.

## Internal Library Inventory

| Library / Namespace         | Observed Purpose     | Evidence                             | Confidence | Unknowns                |
| --------------------------- | -------------------- | ------------------------------------ | ---------- | ----------------------- |
| `com.acme.platform.config`  | Config loading       | `Main.java`, `AppConfig.java`, tests | Medium     | Exact precedence rules  |
| `com.acme.platform.rpc`     | RPC server bootstrap | `Main.java`, `UserRpcService.java`   | Medium     | Threading and lifecycle |
| `com.acme.platform.metrics` | Metrics registration | `MetricsModule.java`                 | Low        | Cardinality conventions |

## Build and Test Commands

| Task            | Command           | Evidence                        | Notes                                  |
| --------------- | ----------------- | ------------------------------- | -------------------------------------- |
| Full validation | `./gradlew check` | `.github/workflows/ci.yml`      | Canonical CI command                   |
| Unit tests      | `./gradlew test`  | Gradle Java plugin and CI check | Candidate if faster feedback is needed |
| Build           | `./gradlew build` | Gradle standard lifecycle       | Candidate, not directly seen in CI     |

## Runtime Entrypoints

| Entrypoint           | Type              | Evidence                                | Notes                             |
| -------------------- | ----------------- | --------------------------------------- | --------------------------------- |
| `com.acme.user.Main` | Service bootstrap | `src/main/java/com/acme/user/Main.java` | Uses internal RPC/config wrappers |

## Risk Areas

| Risk Area            | Evidence                      | Safe Handling                        |
| -------------------- | ----------------------------- | ------------------------------------ |
| Auth/security        | `AuthInterceptor.java`        | Do not change without focused review |
| Production config    | `conf/production.ini`         | Do not modify during onboarding      |
| Generated code       | `build/generated/**`          | Do not edit manually                 |
| Internal RPC wrapper | `com.acme.platform.rpc` usage | Infer from existing usage only       |

## Recommended Next Files to Inspect

1. `src/main/java/com/acme/user/Main.java` — runtime bootstrap.
2. `src/main/java/com/acme/user/rpc/UserRpcService.java` — service API boundary.
3. `src/test/java/com/acme/user/rpc/UserRpcServiceTest.java` — expected behavior and test conventions.
4. `build.gradle` — dependency and task definitions.
5. `.github/workflows/ci.yml` — canonical validation.

## Open Questions

1. What internal documentation defines `com.acme.platform.rpc` lifecycle behavior?
2. Are `conf/staging.ini` and `conf/production.ini` generated or manually maintained?
3. Is `./gradlew check` safe to run locally without internal credentials?

## Safe Next Action

Continue read-only inspection of runtime bootstrap and test examples before proposing any implementation changes.
