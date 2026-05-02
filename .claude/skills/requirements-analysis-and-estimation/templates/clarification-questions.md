---
purpose: Structured clarification output template and domain question banks for pre-analysis ambiguity gathering
load-when: Clarification mode or pre-analysis question gathering
---

# Clarification Questions

Use this template in Clarification mode.
Produce the structured output below first, then draw questions from the question banks in section 3.

---

## Structured Output (Clarification Mode)

### 1. What I Already Understand

Briefly summarize the parts of the request that are already clear: business goal, target users, known constraints, trigger events, and expected outcome.

-
-
-

### 2. What Is Still Ambiguous

List uncertainties that would materially affect architecture, business logic, scope, data model, test strategy, or rollout.

-
-
-

### 3. Clarifying Questions

Group by theme. For each question, include why it matters, the main options, and the recommended default.

**[Theme: e.g., Scope / Data / Permissions / Integration / Non-Functional]**

**Q1: [Question]**

- **Why it matters:**
- **Main options:**
  - A:
  - B:
- **Recommended default:** A — [brief reason]

---

### 4. Tentative Defaults

Assumptions you would apply if the user does not answer every question.

| Assumption | Why reasonable | Risk if wrong |
|------------|----------------|---------------|
| | | |

### 5. Readiness for Planning

State one of:

- **Ready for planning** — enough context to proceed.
- **Ready for planning with explicit assumptions** — can proceed; list which assumptions are load-bearing.
- **Not ready yet** — questions in section 3 must be answered before a correct design is possible.

---

## Question Banks

Use these as a source when selecting questions for section 3 above.
Pick only questions that would materially affect implementation or scope; skip the rest.

### Blocking Questions (must answer before implementation)

1. What is the exact action, trigger, or state change being requested? ("User can manage X" is not enough — what can they do, to what entity, under what condition?)
2. Who is the actor and what permission or role is assumed? (anonymous, authenticated user, admin, service-to-service?)
3. What existing system, data model, or API contract does this modify or extend?

### Product / Business

- Who is the target user?
- What problem are we solving?
- What user-visible behavior should change?
- What should remain unchanged?
- What is the success metric?
- What is the release priority?

### Functional

- What are the valid inputs?
- What are the invalid inputs?
- What are the expected outputs?
- What states can the entity move through?
- What actions are allowed?
- What actions are prohibited?
- What happens on duplicate requests?
- What happens when data is missing?

### Non-Functional

- What latency or throughput is expected?
- What reliability level is required?
- What data retention rules apply?
- What audit or traceability is required?
- What security or permission constraints apply?
- What compatibility constraints apply?

### Integration

- Which systems are involved?
- Which API owns the source of truth?
- What happens if an upstream dependency fails?
- What happens if a downstream dependency rejects the request?
- Is retry safe?
- Is idempotency required?

### Data

- What data is created?
- What data is updated?
- What data is deleted?
- Is migration required?
- Is rollback required?
- Are there privacy or sensitive-data concerns?

### Testing

- What is the minimum acceptance test?
- What regression risks matter most?
- What existing tests cover similar behavior?
- What manual QA is required?
