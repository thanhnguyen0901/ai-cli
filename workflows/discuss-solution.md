# Discuss Solution Workflow

## State
- `DISCUSS`

## Purpose
- Accept clarifications and refine solution proposal without losing agreed decisions.
- Keep discussion controlled and traceable.

## Accepted Clarification Inputs
- Business detail updates.
- Expected behavior corrections.
- Selector corrections.
- HTML snippets / DOM fragments.
- UI structure clarifications.
- Existing code references.

## Procedure
1. Capture new clarification input and classify its type.
2. Compare clarification against current analysis and proposal.
3. Update proposal sections impacted by the new input:
   - business flow interpretation,
   - selector strategy,
   - reuse vs new code,
   - file impact and risks.
4. Preserve already agreed points unless explicitly revised by user.
5. Present a concise `Delta Summary` showing what changed and why.
6. Ask whether clarification should be persisted to context/memory:
   - `Should this clarification be recorded in context/memory? (yes/no)`
7. If `yes`, queue `UPDATE CONTEXT` after current review step.
8. Return to `ANALYZE + SOLUTION REVIEW` workflow (`workflows/generate-test.md`) at its solution review decision point.

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
  - `New Clarifications`
  - `Delta Summary`
  - `Updated Proposal Snapshot`
  - `Context/Memory Update Prompt`
  - `Required User Decision`
  - `Next Allowed Commands`

## Guardrails
- Do not generate code in discussion workflow.
- Do not discard prior agreed requirements silently.
- Do not persist unverified claims as facts.

## Exit Condition
- Updated solution review is presented.
- Control returns to `workflows/generate-test.md` review options.
