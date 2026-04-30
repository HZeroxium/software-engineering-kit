# Output Standards

## General Standards

- Be concise but complete.
- Prefer structured headings and bullets for technical answers.
- Avoid generic praise and filler.
- Lead with the recommendation when clear.
- Separate facts from assumptions.
- Include trade-offs when options exist.
- Include validation and risk notes for engineering tasks.
- Do not invent commands, APIs, versions, framework behavior, paths, or test results.

## Standard Engineering Answer Format

Use this structure when useful:

### Assumptions

- State assumptions that affect the answer.
- Omit this section for very small answers when there are no meaningful assumptions.

### Recommended Approach

- Provide the practical recommendation.
- Explain why it is preferred.
- Mention important trade-offs.

### Minimal Fix

- Show the smallest safe change when applicable.
- Preserve existing style.
- Avoid broad rewrites.

### Validation Plan

- List tests or checks to run.
- Prefer commands discovered from the repo.
- State when commands are assumed rather than confirmed.

### Risks and Edge Cases

- Call out correctness, security, concurrency, data consistency, performance, observability, maintainability, and testability risks.

### Tests Run / Tests Not Run

- State what was run.
- State what was not run and why.
- Do not claim tests passed unless they actually ran or the user provided the result.

### Next Steps

- Provide only useful next steps.
- Avoid long generic lists.

## Code Review Format

For code review, critique before rewriting.

Use severity levels:

### Blocking

Issues that must be fixed before merge:

- Correctness bugs
- Security vulnerabilities
- Data loss risks
- Broken API contracts
- Unsafe concurrency
- Failing build/tests
- Production-impacting regressions

### Important

Issues that should usually be fixed:

- Maintainability problems
- Missing important tests
- Observability gaps
- Performance risks
- Weak error handling
- Ambiguous behavior
- Risky coupling

### Optional

Nice-to-have improvements:

- Small readability improvements
- Minor refactors
- Naming improvements
- Documentation improvements
- Non-critical cleanup

For each finding, include:

- Issue
- Evidence
- Impact
- Minimal fix
- Suggested validation

## Debugging Format

For debugging, separate:

### Evidence

- Error messages
- Stack traces
- Logs
- Reproduction steps
- Recent changes
- Environment details

### Hypotheses

- Plausible causes ordered by likelihood and impact.

### Experiments

- Specific checks to confirm or reject each hypothesis.

### Root Cause

- State only when supported by evidence.

### Fix

- Minimal safe fix.
- Avoid broad rewrites.

### Regression Test

- Test that prevents recurrence.

## Planning Format

For implementation planning, include:

### Scope

- What will change.
- What will not change.

### Affected Files / Modules

- List known affected areas.
- Mark unknowns explicitly.

### Implementation Steps

- Small, reviewable steps.

### Risks

- Correctness
- Security
- Data
- Concurrency
- Performance
- Observability
- Compatibility
- Operations

### Validation

- Targeted checks first.
- Broader checks when needed.
- Manual review for high-risk changes.

### Rollback

- How to revert or disable the change.
- Data rollback notes when applicable.

## Documentation Output

For documentation tasks:

- Ground claims in current code, configs, tests, scripts, APIs, or user-provided requirements.
- Avoid stale claims.
- Avoid invented commands.
- Avoid idealized architecture unless clearly labeled as proposed architecture.
- Use clear headings.
- Prefer copy-ready Markdown.
- Include assumptions and open questions when needed.

## Artifact Output

For AI artifacts, prompts, rules, Skills, agents, or workflow docs:

- Define purpose.
- Define trigger.
- Define inputs.
- Define outputs.
- Define boundaries.
- Define permissions or non-permissions.
- Define failure behavior.
- Define validation.
- Define owner or maintenance expectation when relevant.
- Avoid duplicated or conflicting instructions.
