# Internal Library Checklist

## Detection

- [ ] Internal package prefixes found.
- [ ] Internal build dependencies found.
- [ ] Internal build plugins found.
- [ ] Internal scripts found.
- [ ] Internal generated-code tools found.
- [ ] Custom annotations/decorators found.
- [ ] Custom base classes found.
- [ ] Custom factories/builders found.
- [ ] Custom config loaders found.
- [ ] Custom logging/metrics/tracing wrappers found.
- [ ] Custom test harnesses found.

## Evidence

For each internal library:

- [ ] Production usages found.
- [ ] Test usages found.
- [ ] Example usages found.
- [ ] Documentation found.
- [ ] Initialization path identified.
- [ ] Configuration keys/files identified.
- [ ] Error-handling pattern identified.
- [ ] Testing pattern identified.
- [ ] Owner/version/source unknowns listed.

## Risk Review

- [ ] Handles authentication or authorization.
- [ ] Handles secrets, tokens, certificates, or credentials.
- [ ] Handles database access or migrations.
- [ ] Handles external writes.
- [ ] Handles deployment or infrastructure.
- [ ] Handles generated code.
- [ ] Handles observability instrumentation.
- [ ] Has unclear behavior.
- [ ] Has no tests/examples.
- [ ] Has conflicting usage patterns.

## Safe Handling

- [ ] Do not invent APIs.
- [ ] Do not replace wrappers with raw external libraries without approval.
- [ ] Prefer existing patterns.
- [ ] Ask for internal docs if behavior is unclear.
- [ ] Mark all unconfirmed behavior as unknown.
