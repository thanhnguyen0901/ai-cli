# Setup Project Workflow

## State
- `SETUP`

## Purpose
- Define system behavior immediately after `START`.
- Confirm AI-CLI readiness, detect current knowledge state, and route to learn/refresh decision.

## Preconditions
- `START` trigger received.
- Bootstrap load order already executed: `config -> rules -> workflows -> frameworks -> context -> memory`.

## Inputs
- Loaded system files and runtime config.
- Current repository filesystem state.
- Existing `context/` and `memory/` documents (if present).

## Procedure
1. Confirm startup mode: `AI-CLI Startup`.
2. Report load status for each layer (`LOADED`, `LOADED_WITH_WARNINGS`, `MISSING`, `ERROR`).
3. Validate `context/` and `memory/` presence and basic readability.
4. Report context/memory status:
   - availability,
   - freshness risk,
   - known gaps,
   - missing critical documents (if any).
5. Prompt user explicitly:
   - `Do you want to learn or refresh the current codebase now? (yes/no)`
6. Wait for explicit user response.

## Branching Logic

### If User Selects `yes`
- Transition to `LEARN`.
- Execute `workflows/learn-codebase.md`.
- On completion, transition to `READY` and show main menu.

### If User Selects `no`
- Mark learning status as `SKIPPED_BY_USER`.
- Continue with currently loaded context/memory.
- Report that codebase remains source of truth and memory may be stale.
- Transition directly to `READY` and show main menu.

## Output Contract
- Required response sections:
  - `State`
  - `Load Status`
  - `Context/Memory Status`
  - `Learning Decision Prompt`
  - `Next State`

## Guardrails
- Do not auto-run learning without explicit `yes`.
- Do not generate test code in this workflow.
- Do not run unrelated actions before menu selection in `READY`.

## Exit Condition
- `State: READY`
- Main menu displayed from `main-menu.md`.
