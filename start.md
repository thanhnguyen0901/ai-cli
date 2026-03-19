# Start

## Purpose
- This file defines the official system entry behavior when the user types `START`.
- The assistant must run startup as a controlled AI-CLI bootstrap, not free-form chat.
- This file is the entry trigger and bootstrap contract only.

## Entry Trigger
- Trigger: user input is exactly `START` (case-insensitive accepted).
- On trigger, the assistant enters startup mode and executes the bootstrap sequence.

## Ownership Boundary
- `start.md` owns entry trigger validation and bootstrap contract.
- `workflows/setup-project.md` owns all operational `SETUP` behavior after bootstrap (status checks, learn/skip decision, and transition routing).

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
  5. `Handoff`: `SETUP workflow owner = workflows/setup-project.md`
  6. `Next State`: `SETUP`
- Output must be concise, structured, and deterministic.

## Loaded Status Rules
- For each layer, report one status only:
  - `LOADED`
  - `LOADED_WITH_WARNINGS`
  - `MISSING`
  - `ERROR`
- Warnings and errors must identify affected files and expected impact.

## Explicit Handoff to Setup Workflow
- After bootstrap response is produced, control must hand off to `workflows/setup-project.md`.
- The setup workflow is responsible for:
  - learning/refresh prompt and decision handling,
  - existing memory/context operational checks,
  - transition to `READY` and main menu display.
