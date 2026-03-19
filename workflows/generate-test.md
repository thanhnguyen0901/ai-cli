# Generate Test Workflow

## State
- `ANALYZE + SOLUTION REVIEW`

## Purpose
- Convert manual test intent into a structured, reviewable pre-generation plan.
- Implement the combined-state artifact for logical `ANALYZE` and `SOLUTION REVIEW`.
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

## Minimum Output Contract (Shared)
- Every workflow response must include:
  - `Workflow Name`
  - `Current State`
  - `Objective`
  - `Inputs Consumed`
  - `Analysis Summary`
  - `Risks`
  - `Proposed Action`
  - `Required User Decision`
  - `Next Allowed Commands`
  - `Context Update Needed`
- If a field is not applicable in this workflow, return it as `N/A` instead of omitting it.

## Output Contract
- Required response sections:
  - `Current State`
  - `Test Analysis`
  - `Solution Proposal`
  - `Reuse vs New Code`
  - `Risks`
  - `Required User Decision`
  - `Next Allowed Commands`

## Guardrails
- No code generation is allowed in this workflow.
- Do not assume selectors/business rules without evidence.
- If key inputs are missing, request clarification before proposing approval.

## Exit Condition
- Transition based on user choice:
  - option `1` -> `APPROVE + GENERATE` workflow (`workflows/approve-generate.md`)
  - option `2` -> `DISCUSS` (`workflows/discuss-solution.md`) then return to this workflow's solution review point
  - option `3` -> `EXPLAIN` (`workflows/explain-solution.md`) then return to this workflow's solution review point
