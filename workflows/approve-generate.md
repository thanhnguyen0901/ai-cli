# Approve Generate Workflow

## State
- `APPROVE -> GENERATE`

## Purpose
- Enforce explicit approval gate and controlled transition into code generation.

## Approval Gate Requirements
- Code generation is allowed only after explicit, unambiguous user approval.
- Accepted approval intent includes direct commands such as:
  - `approve`
  - `proceed`
  - `generate now`
- If approval is ambiguous, remain in pre-generation loop.

## Pre-Generation Confirmation
- Confirm framework target (`cypress` or `playwright`).
- Confirm approved task scope and boundaries.
- Confirm reuse-first path and non-duplication intent.

## Checklist Enforcement
- Complete `templates/codegen-checklist-template.md` before generation.
- Any blocked critical item prevents generation.
- If blocked, return to `DISCUSS` or `EXPLAIN` for resolution.

## Generation Execution Rules
- Clearly separate and report:
  - files to modify,
  - files to create.
- Preserve repository architecture, naming conventions, and project style.
- Prefer existing reusable helpers/page objects/commands/fixtures.
- Avoid duplicate abstractions unless explicitly justified by unmet needs.
- Keep change scope minimal and tied to approved request.

## Post-Generation Response
- Provide generation summary with:
  - reused components,
  - new components,
  - modified files,
  - created files,
  - open risks/follow-ups.
- Offer context/memory update step:
  - `Do you want to update context/memory from this change? (yes/no)`

## Guardrails
- Do not generate if approval gate is not passed.
- Do not change unrelated files.
- Do not infer missing selector/business details; return for clarification.

## Exit Condition
- Generation complete and summarized.
- Transition to `CONTEXT UPDATE` (if chosen) or return to `READY` menu.
