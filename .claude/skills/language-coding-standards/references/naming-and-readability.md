# Naming and Readability

## Naming

Good names reveal:

- Domain concept.
- Intent.
- Unit or scale when relevant.
- Ownership.
- Side effect.
- Failure behavior when relevant.

Avoid:

- Generic names like `data`, `info`, `manager`, `processor` without context.
- Misleading names.
- Abbreviations not used by the project.
- Names that expose implementation detail unnecessarily.
- Overly long names that repeat context.

## Function and Method Design

Prefer functions/methods that:

- Do one clear thing.
- Have explicit inputs and outputs.
- Avoid hidden side effects.
- Keep branching understandable.
- Fail clearly.
- Are easy to test.

## Comments

Use comments for:

- Non-obvious intent.
- Business rationale.
- Important trade-offs.
- Compatibility constraints.
- Security constraints.
- Workarounds with reason.

Avoid comments that repeat obvious code.

## Readability

Improve readability by:

- Reducing nested conditionals.
- Using guard clauses when project style supports it.
- Naming intermediate results.
- Keeping abstractions close to use.
- Avoiding clever one-liners.
- Preserving local style.

## Review Questions

- Can another engineer understand this in code review?
- Does the name match behavior?
- Is there a simpler expression?
- Is the abstraction necessary?
- Are important assumptions visible?
