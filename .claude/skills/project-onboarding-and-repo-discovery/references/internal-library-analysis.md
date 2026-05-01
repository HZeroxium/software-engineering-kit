# Internal Library Analysis

## Goal

Understand internal libraries from actual repository evidence without hallucinating their APIs or behavior.

## What Counts as an Internal Library

Treat as internal when a dependency, package, namespace, import, annotation, plugin, wrapper, or script appears organization-specific, unpublished, private, or undocumented externally.

Examples:

- Company-specific package prefixes.
- Custom framework wrappers.
- Private build plugins.
- Internal RPC libraries.
- Internal config systems.
- Internal logging/metrics wrappers.
- Internal testing harnesses.
- Generated-code tooling.
- Internal CI/CD utilities.

## Analysis Method

### 1. Inventory Namespaces

Find repeated:

- Imports.
- Package prefixes.
- Build dependencies.
- Plugins.
- Annotations/decorators.
- Base classes.
- Factory methods.
- Config keys.
- Script names.

### 2. Find Usage Clusters

For each internal symbol:

- Search production usage.
- Search tests.
- Search examples.
- Search docs.
- Search generated code references.

### 3. Infer From Behavior, Not Names

Prefer:

- How the symbol is constructed.
- What arguments it receives.
- How returned objects are used.
- How errors are handled.
- How tests mock/fake it.
- How config drives it.
- How startup wires it.

Avoid:

- Assuming external framework equivalence.
- Assuming annotation semantics.
- Assuming lifecycle behavior.
- Assuming thread-safety.
- Assuming transaction behavior.
- Assuming retry behavior.
- Assuming security behavior.

### 4. Classify Confidence

- **High:** Multiple production usages plus tests/docs agree.
- **Medium:** Production usage is clear but tests/docs are limited.
- **Low:** Only imports, names, or one usage example exist.
- **Unknown:** No reliable usage evidence.

### 5. Output Required Details

For each internal library:

- Name/namespace.
- Observed purpose.
- Evidence files.
- Common usage pattern.
- Initialization path.
- Configuration path.
- Testing pattern.
- Risks.
- Unknowns.
- Recommended next files.

## Red Flags

Escalate when:

- Internal library handles auth, permissions, secrets, encryption, tokens, production access, DB migrations, external writes, or deployment.
- Behavior is hidden behind generated code.
- Docs conflict with code.
- Tests are absent.
- Existing usage is inconsistent.
- The user asks to replace an internal abstraction with a raw external library.
