# Test Harness Discovery

## Objective

Find how the repository verifies behavior and how future changes should be tested.

## Discovery Sources

Inspect:

- Test directories.
- Build files.
- Test framework dependencies.
- CI/CD test steps.
- Test config files.
- Fixtures.
- Test base classes.
- Mock/fake utilities.
- Containerized test dependencies.
- Integration test modules.
- End-to-end test setup.

## Test Types to Identify

| Test Type         | Signals                                                               |
| ----------------- | --------------------------------------------------------------------- |
| Unit tests        | Small tests near source, standard test framework                      |
| Integration tests | External services, DB, containers, network, modules named integration |
| Contract tests    | API schemas, RPC contracts, pact-like tools, generated stubs          |
| E2E tests         | Browser/API flows, deployed environment assumptions                   |
| Smoke tests       | Health checks, startup checks, minimal validation                     |
| Performance tests | Load scripts, benchmarks, profiling configs                           |
| AI/eval tests     | Golden datasets, evaluation scripts, metrics reports                  |

## Java Examples

Look for:

- JUnit 4/5.
- TestNG.
- Mockito.
- AssertJ.
- Hamcrest.
- Maven Surefire/Failsafe.
- Gradle test tasks.
- Testcontainers.
- Embedded databases.
- Internal test base classes.
- Fixture builders.

Do not assume any of these unless files confirm them.

## Python Examples

Look for:

- pytest.
- unittest.
- tox/nox.
- fixtures.
- monkeypatch/mocks.
- eval scripts.
- model test datasets.

## TypeScript Examples

Look for:

- Jest.
- Vitest.
- Playwright.
- Cypress.
- Testing Library.
- TypeScript typecheck scripts.

## Output Requirements

Report:

- Test frameworks confirmed.
- Test directory layout.
- Test command evidence.
- Required local dependencies.
- Slow/integration tests.
- Fixtures and helper patterns.
- Missing test signals.
- Recommended test strategy for future changes.

## Safety

Do not run tests that require external credentials, production systems, database migrations, or destructive fixtures without user approval.
