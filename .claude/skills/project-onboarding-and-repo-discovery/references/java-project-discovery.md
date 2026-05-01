# Java Project Discovery

## Objective

Use Java as the primary example language while remaining framework-agnostic.

## High-Signal Files

Look for:

- `pom.xml`
- `build.gradle`
- `build.gradle.kts`
- `settings.gradle`
- `settings.gradle.kts`
- `gradle.properties`
- `mvnw`, `mvnw.cmd`
- `gradlew`, `gradlew.bat`
- `.mvn/**`
- `src/main/java/**`
- `src/test/java/**`
- `src/integrationTest/**`
- `src/main/resources/**`
- `src/test/resources/**`
- `module-info.java`
- `Dockerfile`
- `Jenkinsfile`
- `.github/workflows/**`

## Build System Signals

### Maven

Evidence:

- `pom.xml`
- parent POMs
- modules
- plugins
- profiles
- wrapper files

Candidate commands:

- `./mvnw test`
- `./mvnw verify`
- `./mvnw -pl <module> test`
- `mvn test`
- `mvn verify`

Only classify commands as confirmed if the repo documents them or CI uses them.

### Gradle

Evidence:

- `settings.gradle`
- `build.gradle`
- Gradle wrapper files
- subprojects
- tasks
- plugins

Candidate commands:

- `./gradlew test`
- `./gradlew check`
- `./gradlew build`
- `./gradlew :<module>:test`

Only classify commands as confirmed if the repo documents them or CI uses them.

## Runtime Entrypoint Signals

Look for:

- `public static void main(String[] args)`
- Application bootstrap classes.
- Server factories.
- CLI command classes.
- Worker startup.
- Scheduler startup.
- Internal server wrappers.
- Service registration.
- Dependency injection modules.
- Config initialization.

Do not assume Spring Boot from Java alone. Confirm through dependencies, annotations, plugins, resource files, and startup code.

## Internal Java Patterns

Search for:

- Company package prefixes.
- Custom annotations.
- Base service classes.
- Interceptors/filters/middleware.
- RPC stubs/wrappers.
- Config readers.
- Logging and metrics wrappers.
- Dependency injection modules.
- Test base classes.
- Fixtures and embedded service utilities.

## Java Risk Areas

Flag:

- Auth filters/interceptors.
- Token handling.
- Serialization/deserialization.
- Thread pools.
- Transactions.
- Database migrations.
- External clients.
- Retry policies.
- Timeouts.
- Resource cleanup.
- Observability cardinality.
- Reflection.
- Generated sources.
- Annotation processors.

## Java Output Notes

When reporting Java findings:

- Prefer package/class names with paths.
- Distinguish module dependencies from runtime dependencies.
- Identify wrapper APIs and internal conventions.
- List confirmed test command(s) from Maven/Gradle/CI evidence.
- Avoid inventing framework semantics.
