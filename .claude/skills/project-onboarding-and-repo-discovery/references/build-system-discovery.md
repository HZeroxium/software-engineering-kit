# Build System Discovery

## Objective

Identify build, package, dependency, codegen, and validation workflows from repository evidence.

## General Discovery Sources

Inspect:

- README and developer docs.
- Build files.
- Lockfiles.
- Package manager files.
- Wrapper scripts.
- Makefiles.
- Task runners.
- CI/CD files.
- Dockerfiles.
- Compose files.
- Tool config files.
- Scripts directory.

## Common Build Signals

| Ecosystem       | Files                                                                                                |
| --------------- | ---------------------------------------------------------------------------------------------------- |
| Java Maven      | `pom.xml`, `.mvn/**`, `mvnw`                                                                         |
| Java Gradle     | `build.gradle`, `settings.gradle`, `gradlew`                                                         |
| Python          | `pyproject.toml`, `requirements*.txt`, `setup.py`, `tox.ini`, `noxfile.py`, `uv.lock`, `poetry.lock` |
| TypeScript/Node | `package.json`, `package-lock.json`, `pnpm-lock.yaml`, `yarn.lock`, `tsconfig.json`                  |
| Go              | `go.mod`, `go.sum`, `Makefile`                                                                       |
| Rust            | `Cargo.toml`, `Cargo.lock`                                                                           |
| DevOps          | `Makefile`, `Dockerfile`, `docker-compose*.yml`, Helm charts, Terraform files, CI files              |
| AI/ML           | `requirements*.txt`, `pyproject.toml`, notebooks, model configs, training scripts, eval scripts      |

## Command Classification

### Confirmed

A command is confirmed when found in:

- CI/CD.
- README/developer docs.
- Makefile/task runner.
- Package scripts.
- Build tool standard tasks with matching wrapper files.

### Candidate

A command is candidate when:

- It is standard for the build tool but not explicitly documented.
- The repo has expected files but no command evidence.
- A module-specific path is likely but unconfirmed.

### Unsafe Without Approval

Commands are unsafe when they may:

- Deploy.
- Publish artifacts.
- Modify databases.
- Generate code over existing files.
- Upgrade dependencies.
- Delete files.
- Reformat broad code areas.
- Modify infrastructure.
- Write to external systems.

## Output Requirements

For every command, include:

- Command.
- Task.
- Evidence.
- Confidence.
- Side-effect risk.
- Scope, if module-specific.

## Recommended Behavior

- Do not run commands until the user asks.
- Recommend smallest safe validation first.
- Ask before running commands that may mutate files or external systems.
- Prefer `--help`, `tasks`, `list`, or dry-run style discovery when safe.
