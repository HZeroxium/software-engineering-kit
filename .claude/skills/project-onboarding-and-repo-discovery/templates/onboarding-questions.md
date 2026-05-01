# Onboarding Questions

Use these questions after the initial read-only repository scan.

## Purpose and Ownership

1. What is the primary business or engineering purpose of this repository?
2. Which modules are actively maintained?
3. Which modules are legacy, deprecated, generated, or vendor-owned?
4. Who owns architecture decisions for this repository?

## Build and Runtime

1. What is the canonical local build command?
2. What is the canonical test command before submitting changes?
3. Are there internal tools required to build or run this project?
4. Are there environment variables, local services, or credentials required for local execution?
5. Which commands are safe to run locally without side effects?

## Architecture

1. What are the main runtime entrypoints?
2. Is this repo a service, library, CLI, worker, frontend, infrastructure repo, AI application, or mixed repo?
3. What are the main module boundaries?
4. Which abstractions should be reused instead of introducing raw framework APIs?
5. Are there generated-code directories that should not be edited manually?

## Internal Libraries

1. Which internal libraries are approved extension points?
2. Which internal libraries are wrappers around external frameworks?
3. Are there examples or reference modules showing correct usage?
4. Are there internal docs for configuration, RPC, dependency injection, logging, metrics, tracing, or testing utilities?
5. Which internal APIs are unstable or deprecated?

## Safety and Risk

1. Which areas require human approval before changes?
2. Are there production configs, secrets, migrations, infrastructure, or CI/CD files in this repository?
3. Are there customer data, private logs, credentials, or sensitive fixtures?
4. Are there commands that mutate external systems?
5. What is the rollback strategy for risky changes?

## AI Context

1. Should a persistent `docs/ai/repo-map.md` be created?
2. Should this repo use `AGENTS.md`, `CLAUDE.md`, or another repo-level instruction artifact?
3. What should AI assistants never change without approval?
4. What validation command should AI assistants run before claiming completion?
