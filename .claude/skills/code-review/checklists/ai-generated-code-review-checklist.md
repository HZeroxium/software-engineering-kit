# AI-Generated Code Review Checklist

AI-generated code needs stricter review because it may look plausible while hiding incorrect assumptions.

## Grounding

- [ ] Code matches the actual requirement.
- [ ] Code uses real project APIs.
- [ ] Code uses real file paths.
- [ ] Code follows existing project conventions.
- [ ] Code does not invent framework behavior.
- [ ] Code does not invent commands.

## Integration

- [ ] Imports are valid.
- [ ] Dependency versions support used APIs.
- [ ] Public contracts remain compatible.
- [ ] Generated code compiles in the repo context.
- [ ] Error handling matches project patterns.
- [ ] Tests integrate with current test framework.

## Safety

- [ ] No secrets or sensitive data are added.
- [ ] No unsafe shell/database/network behavior is introduced.
- [ ] No broad rewrite is hidden inside the patch.
- [ ] No unapproved dependency upgrade is included.
- [ ] No production config change is hidden.
- [ ] No auth/security behavior is weakened.

## Testing

- [ ] Tests verify behavior, not implementation trivia.
- [ ] Edge cases are included.
- [ ] Negative cases are included.
- [ ] Regression cases are included for fixes.
- [ ] Mocks do not hide important integration behavior.
- [ ] Test data is realistic and safe.

## Maintainability

- [ ] Code is minimal.
- [ ] Naming is clear.
- [ ] Abstractions are necessary.
- [ ] Duplicated logic is avoided.
- [ ] Comments are useful.
