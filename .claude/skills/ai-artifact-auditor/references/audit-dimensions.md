---
purpose: 9 audit dimensions for evaluating any AI artifact — correctness, clarity, consistency, security, maintainability, testability, portability, context efficiency, activation accuracy
load-when: Starting any artifact audit — load this first, before other references
tier: foundational
see-also:
  - artifact-lifecycle.md
---

# Audit Dimensions

## Correctness

- Does the artifact describe real tool behavior?
- Does it avoid invented syntax?
- Does it match current user workflow?
- Does it produce expected outputs?

## Clarity

- Is purpose clear?
- Is activation clear?
- Are inputs and outputs clear?
- Are boundaries clear?
- Is the file easy to skim?

## Consistency

- Does it conflict with `CLAUDE.md`?
- Does it conflict with `rules/*.md`?
- Does it duplicate another Skill or Agent?
- Does terminology match across artifacts?

## Security

- Does it protect secrets?
- Does it treat external content as untrusted?
- Does it define human approval boundaries?
- Does it avoid unsafe automation?
- Does it avoid excessive tool access?

## Maintainability

- Is the artifact small enough?
- Are deep references in supporting files?
- Is ownership clear?
- Are update triggers clear?
- Is naming stable?

## Testability

- Can it be smoke-tested?
- Is expected output visible?
- Are validation prompts included?
- Are failure signs clear?

## Portability

- Is it user-global or repo-specific intentionally?
- Does it avoid unnecessary tool lock-in?
- Does it separate tool-specific syntax from general guidance?

## Context Efficiency

- Is `SKILL.md` concise?
- Are long examples moved to supporting files?
- Is always-loaded content minimal?
- Is duplication removed?

## Activation Accuracy

- Is description specific enough?
- Does it include trigger phrases?
- Does it avoid broad generic phrasing?
- Does it specify when not to use?
