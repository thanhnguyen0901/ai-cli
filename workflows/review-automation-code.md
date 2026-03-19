# Review Automation Code Workflow

## State
- `REVIEW AUTOMATION CODE`

## Purpose
- Review existing automation code for correctness, maintainability, reuse opportunities, and framework alignment.
- Provide a structured review path for main menu option `3`.

## Trigger
- Invoked from `main-menu.md` option `3. Review Existing Automation Code`.

## Accepted Inputs
- Target file path(s) or directory scope.
- Framework context (`cypress`, `playwright`, or auto-detect from files).
- Review focus (for example: reliability, selectors, reuse, style, async handling).
- Optional business scenario context.

## Review Scope
- Readability and scenario clarity.
- Framework-correct syntax and API usage.
- Selector robustness and strategy alignment.
- Assertion quality and business outcome coverage.
- Wait/async handling reliability.
- Reuse of existing helpers/page objects/fixtures/commands.
- Duplication and maintainability risks.
- Fit with repository structure and naming conventions.

## Framework-Aware Review Behavior
- Cypress targets:
  - apply `frameworks/cypress/review-checklist.md` and Cypress adapter guidance.
- Playwright targets:
  - apply `frameworks/playwright/review-checklist.md` and Playwright adapter guidance.
- Mixed scope:
  - review each file with framework-correct checklist and avoid cross-framework assumptions.

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
  - `Scope Reviewed`
  - `Framework Detected`
  - `Findings (ordered by severity)`
  - `Reuse Opportunities`
  - `Risks`
  - `Proposed Action`
  - `Required User Decision`
  - `Next Allowed Commands`

## Guardrails
- This workflow is review-only and must not generate new code automatically.
- If changes are requested, route user to the controlled generation lifecycle.
- Do not claim issues without file-based evidence.

## Exit Condition
- Review output delivered.
- Return to `READY` state and re-display main menu.
