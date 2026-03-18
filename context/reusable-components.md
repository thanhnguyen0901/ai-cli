# Reusable Components Context

## Purpose
- Track reusable automation building blocks that AI-CLI should prioritize during solution planning and code generation.
- Provide a consistent inventory structure that can be enriched after learning.

## Component Categories to Track
- Page objects.
- Navigation helpers.
- Authentication helpers.
- Assertion helpers.
- Data builders/fixtures.
- Modal/dialog helpers.
- Table/form helpers.
- API/wait synchronization helpers.

## Reuse Priority Rules
- Prefer existing reusable components before proposing new code.
- Reuse is mandatory when component behavior already matches requested flow.
- New components are allowed only when no existing component satisfies requirements.

## Documentation Schema
- For each reusable asset, capture:
  - `Name`
  - `Category`
  - `Source File`
  - `Supported Actions`
  - `Framework Scope` (`cypress`, `playwright`, `shared`)
  - `Usage Constraints`
  - `Stability` (`stable`, `evolving`, `deprecated`)

## Stable vs Temporary Asset Rules
- Stable asset:
  - used across multiple scenarios,
  - consistent interface,
  - low churn.
- Temporary helper:
  - one-off scenario utility,
  - incomplete abstraction,
  - high likelihood of removal/change.
- Temporary helpers should not be treated as default reuse targets.

## Post-Learning Enrichment Rules
- Populate component inventory from actual code references.
- Merge duplicates that represent equivalent behavior.
- Flag gaps where repeated logic exists without reusable abstraction.
- Record ownership and preferred usage patterns when inferable from code.
