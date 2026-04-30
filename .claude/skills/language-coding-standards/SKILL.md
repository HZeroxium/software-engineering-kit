---
name: language-coding-standards
description: Use when implementing, refactoring, or reviewing code style, syntax, idioms, language-level design, production-grade class/function/module structure, or maintainability in Java, Python, TypeScript, frontend, backend, DevOps, or AI application code. Prefer repository conventions and existing language/runtime version over generic rewrites.
---

# Language Coding Standards

## Purpose

Guide implementation and review for idiomatic, maintainable, type-safe, testable, production-grade code.

Primary focus: Java backend.  
Also supports: Python, TypeScript, frontend-aware TypeScript, DevOps scripts, and AI application code.

This Skill is instruction-only. It does not enforce style, run hooks, configure MCP, create agents, or define repo-specific commands.

## When to use

Use this Skill when the user asks to:

- Implement code.
- Refactor code.
- Review implementation style.
- Choose language idioms.
- Improve syntax or readability.
- Write production-grade functions, classes, services, modules, or utilities.
- Work in Java, Python, TypeScript, or mixed-stack codebases.

## When not to use

Do not use this Skill for:

- Pure architecture review unless code-level implementation standards are the focus.
- Pure debugging unless implementation style contributes to the bug.
- Pure documentation without code implications.
- Adding new libraries without user approval.
- Inventing framework-specific conventions.

## Required inputs

Useful inputs include:

- Target language and runtime version.
- Existing files and nearby style.
- Build/dependency files.
- Tests.
- API contracts.
- Error handling conventions.
- Logging conventions.
- Framework conventions.
- User acceptance criteria.
- Validation commands discovered from the repo.

## Workflow

1. Inspect or infer existing repo conventions before proposing style changes.
2. Identify language, runtime version, framework, and project style from repo evidence when available.
3. Separate confirmed facts from assumptions.
4. Preserve public contracts unless behavior change is explicitly requested.
5. Prefer minimal, idiomatic code.
6. Avoid new libraries unless justified and user-approved.
7. Apply language-specific guidance:
   - Java: class/interface design, null handling, exceptions, collections, generics, concurrency, resource lifecycle, DTO/domain/entity boundaries, DI boundaries, logging, testability.
   - Python: type hints, dataclasses/Pydantic when appropriate, async correctness, error handling, timeouts/retries, logging, testability.
   - TypeScript: strict typing, runtime validation for external input, null/undefined handling, API contracts, async error handling, module boundaries, frontend awareness, testability.
8. Include edge cases and failure modes.
9. Include validation plan: compile/typecheck/tests/lint/static analysis as applicable.
10. Do not invent APIs, commands, versions, or framework behavior.

## Output format

Default output:

```markdown
# Implementation Guidance

# Confirmed Facts

# Assumptions

# Recommended Approach

# Minimal Code / Fix Plan

# Edge Cases and Failure Modes

# Validation Plan

# Risks and Trade-offs
```

For code review:

```markdown
# Language-Specific Review

# Findings

# Minimal Fixes

# Validation
```

## Safety boundaries

- Do not invent APIs, commands, framework behavior, file paths, or dependency versions.
- Do not introduce new libraries without justification and user approval.
- Do not rewrite broadly unless explicitly requested.
- Preserve public API, schema, behavior, and compatibility unless change is requested.
- Do not expose secrets, credentials, customer data, sensitive logs, or proprietary data.
- Require explicit confirmation before high-risk changes involving migrations, auth/security, CI/CD, production configs, dependency upgrades, destructive operations, infrastructure, or broad rewrites.

## Validation

Recommend validation through:

- Java compile/test/static analysis.
- Python typecheck/test/lint/static analysis.
- TypeScript typecheck/test/lint/build.
- Framework-specific tests only when discovered from repo.
- Logs/metrics/traces when runtime behavior changes.
- Manual review for security-sensitive changes.

- Do not invent commands. Discover commands from the current repository.

## Failure handling

If repository conventions are unclear:

- State uncertainty.
- Follow conservative language defaults.
- Avoid adding dependencies.
- Ask targeted questions only when required.
- Prefer minimal local changes.

## Supporting files

Load only when useful:

- references/java-coding-standards.md
- references/python-coding-standards.md
- references/typescript-coding-standards.md
- references/error-handling-standards.md
- references/dependency-and-library-usage.md
- references/naming-and-readability.md
- references/immutability-and-state.md
- references/concurrency-and-async.md
- templates/implementation-guidance.md
- templates/language-specific-review.md
- templates/coding-standard-fix-plan.md
- examples/java-service-method-example.md
- examples/python-service-function-example.md
- examples/typescript-module-example.md
- checklists/java-implementation-checklist.md
- checklists/python-implementation-checklist.md
- checklists/typescript-implementation-checklist.md
