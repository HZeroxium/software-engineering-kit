---
purpose: Actionable pass/fail checklist for reviewing accuracy, completeness, maintainability, safety, and reader experience of documentation
load-when: Reviewing or finalizing any documentation artifact
tier: domain
see-also:
  - references/docs-from-source-of-truth.md
---

# Documentation Review Checklist

## Accuracy

- [ ] Claims are grounded in current source-of-truth evidence.
- [ ] Current and proposed behavior are separated.
- [ ] Commands are verified or marked as assumptions.
- [ ] APIs, schemas, and configs match current files.
- [ ] Known limitations are documented.
- [ ] Open questions are visible.

## Completeness

- [ ] Purpose is clear.
- [ ] Audience is clear.
- [ ] Scope is clear.
- [ ] Inputs and outputs are clear.
- [ ] Error behavior is covered.
- [ ] Security impact is covered.
- [ ] Observability impact is covered.
- [ ] Testing or validation is covered.
- [ ] Rollback or disable path is covered when relevant.

## Maintainability

- [ ] Document location is appropriate for the target audience.
- [ ] Duplicate content is minimized.
- [ ] Stale sections are removed or updated.
- [ ] Terminology is consistent.

## Safety

- [ ] No secrets or sensitive data are included.
- [ ] No unsafe commands are presented without caution.
- [ ] Production-impacting procedures require review.
- [ ] Auth/security changes are not oversimplified.
- [ ] Customer data handling is explicit when relevant.

## Reader Experience

- [ ] Summary appears near the top.
- [ ] Headings are clear.
- [ ] Tables are used for structured comparisons.
- [ ] Examples are realistic.
- [ ] Action items are explicit.
- [ ] Long docs include navigation or sections.
