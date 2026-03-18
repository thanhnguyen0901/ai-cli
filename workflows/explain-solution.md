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

## Output Contract
- Required response sections:
  - `State`
  - `Detailed Mapping`
  - `Reuse Rationale`
  - `File Impact Rationale`
  - `Selector/Assertion/Async Strategy`
  - `Risks and Tradeoffs`
  - `Next Options`

## Guardrails
- Explanation must not include generated implementation code.
- Do not bypass approval gate while explaining.
- Do not convert explanation into execution without explicit approval.

## Exit Condition
- Control returns to `SOLUTION REVIEW` options with updated user clarity.
