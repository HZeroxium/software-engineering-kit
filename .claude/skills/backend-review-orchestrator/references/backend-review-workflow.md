---
purpose: Expanded step-by-step procedure for executing a full multi-scope backend review pass
load-when: Executing a structured multi-scope review — provides detailed inspection procedure per step
tier: domain
see-also:
  - backend-business-logic-correctness.md
---

# Backend Review Workflow

## Workflow

1. **Understand review target**
   - Identify diff, PR, files, design, or AI-generated code.

2. **Classify scopes**
   - Map changes to backend review scopes.

3. **Prioritize production risk**
   - Security, data loss, contract breaks, migrations, outages, and operational blind spots outrank style.

4. **Inspect behavior**
   - Review domain/API behavior, workflow, data, security, integrations, reliability, performance, observability, and tests.

5. **Generate findings**
   - Use Blocking, Important, Optional.

6. **Recommend minimal fixes**
   - Suggest focused changes that reduce risk without broad rewrite.

7. **Define validation**
   - Specify tests, build, typecheck, lint, static analysis, CI, logs, metrics, or manual review.

8. **State remaining risk**
   - Do not imply full approval when validation is missing.
