---
name: language-coding-standards
description: Use when implementing, refactoring, or reviewing Java, Python, or TypeScript code for language idioms, type safety, maintainability, naming/readability, error handling, async/concurrency, dependency usage, or production-grade function/class/module structure. Use for DevOps scripts, frontend code, backend code, or AI application code only when the task is code-level language standards. Do not use for pure architecture, pure debugging, pure testing, hooks/MCP, broad repo policy, or framework invention.
---

# Language Coding Standards

## Purpose

Guide implementation and review for idiomatic, maintainable, type-safe, testable, production-grade code.

Primary focus: Java backend.  
Also supports: Python and TypeScript, including frontend-aware TypeScript. DevOps scripts and AI application code are in scope only when the requested work is code-level language standards.

This Skill is instruction-only. It does not enforce style, run hooks, configure MCP, create agents, or define repo-specific commands.

The frontmatter description is intentionally scoped to code-level standards to avoid false activation for architecture, debugging, testing, hooks, MCP, or repo-policy tasks.

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
- Pure testing or validation design unless code-level testability is the focus.
- Pure documentation without code implications.
- Hooks, MCP, agents, command guards, permissions, or broad repo policy.
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

## Expected Outputs

Output type: `mixed` - select the component that matches the task:

- Implementation guidance: `recommendation` with confirmed facts, assumptions, recommended approach, minimal code or fix plan, edge cases, validation, and risks.
- Language-specific review: `report` with findings, evidence, impact, minimal fixes, and validation.
- Coding-standard fix plan: `plan` with ordered minimal changes, compatibility notes, tests, validation commands, and residual risk.

The headings below are semantic defaults, not a required fixed schema. Adapt them to the task while preserving the declared output type.

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

## Rule coordination

This Skill adds code-level language guidance on top of global rules. Do not duplicate or override:

- `.claude/rules/00-personal-preferences.md` for answer style and general code-work preferences.
- `.claude/rules/10-safety-and-permissions.md` for approval boundaries, secrets, untrusted content, and high-risk actions.
- `.claude/rules/40-harness-engineering-and-validation.md` for validation command discovery and evidence discipline.
- `.claude/rules/50-output-standards.md` for standard engineering and code-review output.

## Safety boundaries

- Do not use language features unavailable in the discovered runtime version.
- Do not introduce new libraries without justification and user approval.
- Do not rewrite broadly unless explicitly requested.
- Preserve public API, schema, behavior, and compatibility unless change is requested.
- When changing logging, errors, or examples, avoid sensitive details and follow global safety rules.

## Validation

Recommend validation through:

- Java compile/test/static analysis.
- Python typecheck/test/lint/static analysis.
- TypeScript typecheck/test/lint/build.
- Framework-specific tests only when discovered from repo.
- Logs/metrics/traces when runtime behavior changes.
- Manual review for security-sensitive changes.

Discover commands from the current repository and mark any assumed commands explicitly.

## Failure handling

If repository conventions are unclear:

- State uncertainty.
- Follow conservative language defaults.
- Avoid adding dependencies.
- Ask targeted questions only when required.
- Prefer minimal local changes.

## Supporting files

Load only what the task needs. Start with `references/reference-index.md` when multiple supporting files may apply or when the load order is unclear.

| File | Purpose | Load when |
| --- | --- | --- |
| `references/reference-index.md` | Semantic navigation graph for references, checklists, templates, and examples | Starting a broad language-standards task, or when unsure which supporting file to load |
| `references/java-coding-standards.md` | Java implementation and review standards | Working in Java code or reviewing Java-specific choices |
| `references/python-coding-standards.md` | Python implementation and review standards | Working in Python code or reviewing Python-specific choices |
| `references/typescript-coding-standards.md` | TypeScript and frontend-aware TypeScript standards | Working in TypeScript code or reviewing TypeScript/frontend code-level choices |
| `references/error-handling-standards.md` | Error taxonomy, boundary mapping, retry classification, and safe logging | Error handling, exception mapping, retry behavior, or failure output is central |
| `references/dependency-and-library-usage.md` | Dependency approval and library selection discipline | Adding, replacing, upgrading, or justifying dependencies |
| `references/naming-and-readability.md` | Naming, method/function shape, comments, and readability checks | Improving clarity, names, comments, or local structure |
| `references/immutability-and-state.md` | Immutability, ownership, lifecycle, and mutable-state risk | Data ownership, state mutation, value objects, DTOs, or concurrency risk matters |
| `references/concurrency-and-async.md` | Java/Python/TypeScript concurrency, async, timeout, retry, and resource rules | Async work, shared state, retries, cancellation, resource lifecycle, or partial failure is involved |
| `templates/implementation-guidance.md` | Structured implementation guidance output | Producing implementation guidance |
| `templates/language-specific-review.md` | Structured language-specific review output | Producing a code-level review report |
| `templates/coding-standard-fix-plan.md` | Structured fix plan output | Producing a minimal coding-standard fix plan |
| `examples/java-service-method-example.md` | Illustrative Java service method example | Calibrating Java guidance or examples |
| `examples/python-service-function-example.md` | Illustrative Python service function example | Calibrating Python guidance or examples |
| `examples/typescript-module-example.md` | Illustrative TypeScript module example | Calibrating TypeScript guidance or examples |
| `checklists/java-implementation-checklist.md` | Java implementation checklist | Reviewing Java implementation completeness |
| `checklists/python-implementation-checklist.md` | Python implementation checklist | Reviewing Python implementation completeness |
| `checklists/typescript-implementation-checklist.md` | TypeScript implementation checklist | Reviewing TypeScript implementation completeness |
