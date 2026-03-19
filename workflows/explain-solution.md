# Explain Solution Workflow

## State
- `EXPLAIN`

## Purpose
- Provide deeper technical rationale for the proposed solution while staying pre-generation.

## Explanation Scope (Mandatory)
- Step mapping from manual instructions to automation actions.
- Reuse choices and why they are preferred.
- File impact (modify vs create).
- Selector strategy and selector risk handling.
- Assertion strategy mapped to expected outcomes.
- Async/wait strategy and synchronization approach.
- Known risks, tradeoffs, and fallback paths.

## Procedure
1. Expand current solution proposal using structured explanation sections.
2. Tie each explanation point to codebase evidence where available.
3. Explicitly call out unresolved assumptions and blockers.
4. Re-present decision options:
   - `1. Approve generate code`
   - `2. Discuss more`
   - `3. Explain in detail (follow-up question)`
5. Wait for explicit user selection.

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
  - `Detailed Mapping`
  - `Reuse Rationale`
  - `File Impact Rationale`
  - `Selector/Assertion/Async Strategy`
  - `Risks`
  - `Required User Decision`
  - `Next Allowed Commands`

## Guardrails
- Explanation must not include generated implementation code.
- Do not bypass approval gate while explaining.
- Do not convert explanation into execution without explicit approval.

## Exit Condition
- Control returns to `ANALYZE + SOLUTION REVIEW` workflow (`workflows/generate-test.md`) review options.
