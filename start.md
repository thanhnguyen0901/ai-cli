# Start

## Purpose
- This file defines the official system entry behavior when the user types `START`.
- The assistant must run startup as a controlled AI-CLI bootstrap, not free-form chat.

## Entry Trigger
- Trigger: user input is exactly `START` (case-insensitive accepted).
- On trigger, the assistant enters startup mode and executes the bootstrap sequence.

## Bootstrap Sequence (Mandatory Order)
- Load order is fixed and must not be changed:
  1. `config/` policy from `config.md`
  2. `rules/` policies
  3. `workflows/` definitions
  4. `frameworks/` guides
  5. `context/` project context files
  6. `memory/` historical memory files
- If any required file is missing or unreadable, report it immediately in startup status.

## Startup Response Contract
- Startup response must use this structure and order:
  1. `Mode`: `AI-CLI Startup`
  2. `Load Status`: per-layer status for config, rules, workflows, frameworks, context, memory
  3. `Configuration Applied`: key runtime settings from `config.md`
  4. `Context/Memory Status`: availability, freshness risk, and known gaps
  5. `Learning Prompt`: ask whether to learn or refresh the current codebase
  6. `Next State`: `SETUP` waiting for user decision
- Output must be concise, structured, and deterministic.

## Loaded Status Rules
- For each layer, report one status only:
  - `LOADED`
  - `LOADED_WITH_WARNINGS`
  - `MISSING`
  - `ERROR`
- Warnings and errors must identify affected files and expected impact.

## Learning/Refresh Decision Prompt
- After loading, the assistant must ask:
  - `Do you want to learn or refresh the current codebase now? (yes/no)`
- The assistant must wait for explicit user response.
- The assistant must not auto-start learning without explicit confirmation.

## Existing Memory Handling
- If memory/context already exist:
  - report that existing knowledge is available,
  - mark it as potentially stale until validated against code,
  - recommend refresh when repository changes are likely.
- Existing memory must be treated as support data, not source of truth.

## If User Declines Learning
- If user answers `no`:
  - keep startup complete,
  - mark learning state as `SKIPPED_BY_USER`,
  - continue with currently loaded rules/context/memory,
  - transition to `READY` and display main menu.

## Transition to Ready/Menu State
- After user decision (learn or skip), startup must end with:
  - `State: READY`
  - main menu display from `main-menu.md`
- The assistant must wait for an explicit menu selection before running any workflow.
