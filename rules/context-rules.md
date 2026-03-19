# Context Rules

## Context vs Memory
- `context/` stores project-specific, operationally useful reference knowledge for active execution.
- `memory/` stores durable historical knowledge, decisions, and longitudinal maps.
- Context is tactical and frequently refreshed; memory is strategic and accumulative.

## Update Triggers

### Update Context When
- New verified codebase patterns are discovered during LEARN.
- Test generation introduces or changes reusable implementation patterns.
- Selector strategy, page object structure, or command usage meaningfully changes.
- Current-context documents are missing facts required for repeatable workflow execution.

### Update Memory When
- A durable architectural or workflow decision is made.
- Reusable maps/indexes become materially richer (helpers, domains, components).
- Significant generation history or recurring gap patterns emerge.
- A decision or risk should influence future sessions beyond the current task.

## Freshness and Reliability Rules
- Treat all context/memory documents as potentially stale until validated against code.
- Memory freshness must be checked during LEARN and before GENERATE for impacted areas.
- If freshness is uncertain, rescan relevant code before relying on stored information.

## Rescan Rules
- Rescan when:
  - repository structure changed,
  - core helpers/commands/page objects changed,
  - selectors or business flow implementation changed,
  - memory/context conflict with observed code.
- Targeted rescans are preferred over full rescans unless uncertainty is broad.

## Conflict Resolution
- If codebase and context/memory disagree, codebase wins.
- The assistant must:
  - flag the conflict,
  - use codebase-backed behavior immediately,
  - queue or apply context/memory correction in `CONTEXT UPDATE`.

## Persistence Policy

### Persist Worthwhile Knowledge
- Stable automation architecture patterns.
- Reusable helper/page-object/custom-command mappings.
- Business flow maps linked to code evidence.
- Selector strategy principles and known reliability constraints.
- Decisions and rationale affecting future test generation.

### Do Not Persist
- Speculation, guesses, or unverified assumptions.
- Temporary debugging chatter.
- User-private or sensitive data not required for automation workflow.
- One-off details with no reuse value.

## Update Format Requirements
- Every context/memory update must be concise, factual, and code-evidenced.
- Required update fields:
  - `Date`
  - `Source Files`
  - `Change Summary`
  - `Impact on Generation`
  - `Update Confidence`
- Optional source-quality field:
  - `Evidence Confidence`
- These fields must be explicitly enforced in:
  - `workflows/update-context.md` output contract,
  - `templates/context-update-template.md`.
- Confidence levels must be explicit: `high`, `medium`, or `low`.
- Low-confidence entries must include a follow-up rescan action.
