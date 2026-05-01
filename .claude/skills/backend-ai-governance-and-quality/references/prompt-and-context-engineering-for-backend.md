# Prompt and Context Engineering for Backend

## Purpose

Build model inputs that are minimal, relevant, safe, and testable.

## Context Rules

- Include only data needed for the task.
- Separate instructions from untrusted data.
- Label retrieved content as untrusted context.
- Do not include secrets or unnecessary sensitive data.
- Keep context bounded.
- Prefer structured context over raw dumps.
- Version important prompt templates.
- Test prompt changes with evaluation cases.

## Prompt Design Questions

- What is the task?
- What output schema is expected?
- What constraints must be followed?
- What context is trusted vs untrusted?
- What should the model refuse or escalate?
- What should happen when information is missing?

## Failure Modes

- Prompt includes excessive private data.
- Retrieved content injects instructions.
- Output is free-form when downstream expects schema.
- Prompt change silently alters production behavior.
- Prompt has no regression tests.
