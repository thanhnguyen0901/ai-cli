# Learn Codebase Workflow

## State
- `LEARN`

## Purpose
- Analyze the current automation repository and extract reusable, code-evidenced project knowledge.
- Refresh local context/memory while preserving codebase-as-source-of-truth policy.

## Preconditions
- User explicitly approved learning/refresh.
- System is in controlled AI-CLI workflow mode.

## Inspection Scope (Mandatory)
- Test folders and spec organization.
- Page objects / screen models.
- Helpers and shared utilities.
- Fixtures and test data assets.
- Custom commands.
- Framework and runner config files.
- Selector patterns and locator strategy.
- Naming conventions for tests and support code.
- Business flow signals embedded in tests, page objects, and helper names.

## Extraction Targets (Mandatory)
- Repository architecture and module boundaries.
- Active framework usage (`cypress`, `playwright`, or both with separation).
- Reusable automation assets.
- Style and assertion conventions.
- Domain/business understanding inferred from code evidence.
- Current gaps, risks, and uncertainty areas.

## Update Targets
- Write tactical, execution-facing findings to `context/` files.
- Write durable, historical decisions/maps to `memory/` files.
- Use structured updates compatible with `templates/context-update-template.md`.

## Stale Memory Handling
- Treat existing context/memory as potentially stale until validated.
- If stale or conflicting with code:
  - flag the conflict,
  - keep codebase-backed interpretation,
  - update context/memory accordingly.

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

## Completion Report Contract
- Required response sections:
  - `Current State`
  - `Sources Scanned`
  - `Framework Usage Detected`
  - `Reusable Assets Identified`
  - `Conventions Identified`
  - `Domain Understanding`
  - `Risks`
  - `Context/Memory Updates Applied`
  - `Proposed Action`
  - `Required User Decision`
  - `Next Allowed Commands`

## Guardrails
- Codebase is always authoritative over stored memory/context.
- Do not fabricate business logic or missing architecture details.
- Do not generate feature/test code in this workflow.

## Exit Condition
- Learning summary complete.
- Transition to `READY`.
