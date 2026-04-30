# Over-Engineering Risks

## Warning Signs

- Creating many artifacts before real usage.
- Creating agents for simple promptable tasks.
- Creating hooks without clear enforcement need.
- Creating MCP without live external data need.
- Duplicating the same guidance in many places.
- Writing long always-loaded rules.
- Creating broad “do everything” Skills.
- Creating agents with unclear ownership.
- Adding maintenance burden without validation.
- Optimizing for artifact completeness instead of workflow value.

## Preferred Progression

1. Normal prompt.
2. Global rule if behavior is stable.
3. Skill if workflow is repeatable.
4. Agent if separate context or specialized tool boundary is useful.
5. Hook if lifecycle enforcement is needed.
6. MCP if controlled live external access is needed.

## Defer When

- Workflow has not repeated.
- Trigger is unclear.
- Output format is unstable.
- Human process is not settled.
- Risk boundary is unclear.
- Existing artifact can be improved instead.

## Avoid When

- Artifact adds more confusion than value.
- Artifact overlaps with existing one.
- Artifact needs constant manual correction.
- Artifact encourages unsafe automation.
- Artifact hides human approval boundaries.
