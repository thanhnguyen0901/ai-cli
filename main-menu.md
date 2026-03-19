# Main Menu

## Purpose
- This file defines the primary CLI menu shown after startup/setup reaches `READY`.
- The assistant must present this menu in a consistent CLI-style format.

## Menu
- `1. Learn or Refresh Codebase`
- `2. Generate Test From Manual Steps`
- `3. Review Existing Automation Code`
- `4. Update Project Context/Memory`
- `5. Explain Current Project Understanding`
- `6. Exit`

## Option Definitions and Workflow Mapping
- `1. Learn or Refresh Codebase`
  - Run learning scan to validate or refresh understanding of repository structure, patterns, and reusable assets.
  - Workflow: `workflows/learn-codebase.md`.
- `2. Generate Test From Manual Steps`
  - Start combined pre-generation workflow: analysis plus solution review, then route to discuss/explain/approve.
  - Workflow: `workflows/generate-test.md`.
- `3. Review Existing Automation Code`
  - Review specified existing automation code for correctness, reuse opportunities, maintainability, and framework alignment.
  - Workflow: `workflows/review-automation-code.md`.
- `4. Update Project Context/Memory`
  - Apply structured updates to `context/` and `memory/` using verified code evidence and current decisions.
  - Workflow: `workflows/update-context.md`.
- `5. Explain Current Project Understanding`
  - Summarize current known architecture, patterns, reusable components, risks, and confidence level.
  - Deterministic inline behavior: execute in `READY` mode (no workflow file transition) by synthesizing `context/` and `memory/` with codebase-as-source-of-truth constraints.
- `6. Exit`
  - End current AI-CLI workflow loop and stop menu-driven operation.

## Selection Rules
- The assistant must always wait for explicit menu selection.
- The assistant must not auto-run any menu action without a user selection.
- Valid selections are `1`, `2`, `3`, `4`, `5`, `6`.
- If selection is invalid, the assistant must report invalid input and reprint the menu.

## Post-Workflow Behavior
- After completing any option workflow (`1` to `5`), the assistant must return to this main menu.
- If user selects `6`, the assistant exits menu loop and confirms termination.
- No implicit exit or implicit action switching is allowed.

## CLI Presentation Contract
- Use consistent output sections:
  - `State: READY`
  - `Menu`
  - `Select Option (1-6)`
- Keep tone direct and operational.
