# Onboarding Checklist

## Repository Boundary

- [ ] Identify current directory.
- [ ] Identify likely repo root.
- [ ] List top-level files and directories.
- [ ] Identify language indicators.
- [ ] Identify build/package manager files.
- [ ] Identify docs.
- [ ] Identify source directories.
- [ ] Identify test directories.
- [ ] Identify config directories.
- [ ] Identify scripts.
- [ ] Identify CI/CD files.
- [ ] Identify deployment files.
- [ ] Identify generated-code directories.

## Documentation

- [ ] Read README.
- [ ] Read contribution/developer docs.
- [ ] Read existing AI instruction files if present.
- [ ] Mark documentation claims that require code confirmation.

## Build and Test

- [ ] Identify build system.
- [ ] Identify package manager.
- [ ] Identify wrapper scripts.
- [ ] Identify test framework.
- [ ] Identify lint/typecheck/format tools.
- [ ] Identify CI validation commands.
- [ ] Separate confirmed vs candidate commands.

## Runtime

- [ ] Identify runtime entrypoints.
- [ ] Identify config loading.
- [ ] Identify API/RPC/worker/CLI/frontend entrypoints.
- [ ] Identify local run commands.
- [ ] Identify environment requirements.

## Architecture

- [ ] Identify modules.
- [ ] Identify dependency direction.
- [ ] Identify shared libraries.
- [ ] Identify generated code.
- [ ] Identify integration boundaries.
- [ ] Identify observability patterns.

## Internal Libraries

- [ ] Identify internal namespaces.
- [ ] Search production usage.
- [ ] Search tests/examples.
- [ ] Identify wrappers and extension points.
- [ ] Mark unknown behavior explicitly.

## Safety

- [ ] Flag auth/security.
- [ ] Flag secrets.
- [ ] Flag migrations.
- [ ] Flag production configs.
- [ ] Flag CI/CD and infrastructure.
- [ ] Flag data deletion/mutation paths.
- [ ] Flag dependency upgrades.
- [ ] Flag generated code.

## Output

- [ ] Produce onboarding report.
- [ ] Produce internal library inventory.
- [ ] Produce build/test command discovery.
- [ ] Produce AI-ready context block.
- [ ] List next files to inspect.
- [ ] List open questions.
- [ ] Recommend safe next action.
