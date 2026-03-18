# Generate Test Workflow

## State
- `ANALYZE TEST`

## Purpose
- Convert manual test intent into a structured, reviewable pre-generation plan.
- Prepare for approval without generating code.

## Preconditions
- System is in `READY` and user selected generate-test path.
- Framework path is known or must be confirmed before planning.

## Inputs Required
- Manual test steps from user.
- Expected outcomes and pass/fail behavior.
- Relevant business context or acceptance criteria.
- Optional references: existing test files, selectors, HTML snippets.

## Procedure
1. Request manual test steps and expected behavior.
2. Populate analysis output using `templates/test-analysis-template.md`.
3. Interpret business scenario and map each manual step to automation actions.
4. Identify dependencies on existing helpers, page objects, commands, fixtures, and patterns.
5. Separate reuse opportunities from net-new code needs.
6. Build solution proposal using `templates/solution-plan-template.md`.
7. Present explicit next options:
   - `1. Approve generate code`
   - `2. Discuss more`
   - `3. Explain in detail`
8. Wait for explicit user selection.

## Output Contract
- Required response sections:
  - `State`
  - `Test Analysis`
  - `Solution Proposal`
  - `Reuse vs New Code`
  - `Open Risks/Unknowns`
  - `Next Options`

## Guardrails
- No code generation is allowed in this workflow.
- Do not assume selectors/business rules without evidence.
- If key inputs are missing, request clarification before proposing approval.

## Exit Condition
- Transition based on user choice:
  - option `1` -> `APPROVE`
  - option `2` -> `DISCUSS`
  - option `3` -> `EXPLAIN`
