# Update Context Workflow

## State
- `CONTEXT UPDATE`

## Purpose
- Persist verified knowledge from learning, clarification, or generation outcomes into local `context/` and `memory/`.

## When to Run
- After codebase learning/refresh.
- After approved generation that produced durable insights.
- After discussion clarifications that materially affect future work.
- On explicit user request from main menu.

## Template Usage
- Use `templates/context-update-template.md` for every update event.
- Each update must include evidence source, classification, `Update Confidence`, and optional `Evidence Confidence`.

## Governance Required Fields (Mandatory)
- Every context/memory update must explicitly include these fields:
  - `Date`
  - `Source Files`
  - `Change Summary`
  - `Impact on Generation`
  - `Update Confidence`
- These fields are required by `rules/context-rules.md` and must be present even when a value is `N/A`.

## Classification Rules
- Update `context/` for tactical, execution-facing, frequently refreshed knowledge.
- Update `memory/` for durable decisions, maps, and historical patterns.
- Update both when information has immediate and long-term value.

## Required Recording Scope
- New verified facts.
- Decisions and rationale.
- Reusable insights/patterns.
- Known limitations and follow-up refresh triggers.

## Conflict Handling
- If new findings conflict with older memory/context:
  - mark conflict explicitly,
  - keep codebase-backed facts,
  - revise stale entries.
- Never allow stale memory to override observed code behavior.

## Persistence Guardrails
- Do not store unverified assumptions.
- Do not store low-value transient discussion noise.
- Do not store sensitive data unrelated to automation operation.

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
  - `Date`
  - `Source Files`
  - `Change Summary`
  - `Impact on Generation`
  - `Update Confidence`
  - `Evidence Confidence` (if source confidence is tracked separately)
  - `Update Reason`
  - `Classification`
  - `Facts/Decisions Added or Revised`
  - `Conflicts Resolved`
  - `Follow-Up Recommendation`
  - `Proposed Action`
  - `Required User Decision`
  - `Next Allowed Commands`

## Exit Condition
- Context/memory updates completed or intentionally skipped.
- Return to `READY` and show main menu.
