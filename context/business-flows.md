# Business Flows Context

## Purpose
- Store stable business flow knowledge that drives automation intent, assertion quality, and test coverage decisions.
- Provide a reusable flow taxonomy that can be updated with verified project behavior.

## Flow Categories to Maintain
- Authentication flows:
  - login/logout,
  - session renewal,
  - password recovery and MFA variants.
- Navigation flows:
  - primary route transitions,
  - cross-module navigation,
  - deep-link and return-path behavior.
- Create/Edit/Delete flows:
  - entity lifecycle operations,
  - draft/save/publish variants,
  - soft-delete/restore behavior.
- Approval/Review flows:
  - review queues,
  - approve/reject transitions,
  - escalation or rework loops.
- Filter/Search flows:
  - query inputs,
  - filter combinations,
  - sort/pagination behavior.
- Role-based behavior:
  - permission differences,
  - role-specific UI visibility,
  - restricted action enforcement.
- Validation/Error flows:
  - required-field validation,
  - API/business-rule errors,
  - recovery messaging and retry paths.

## Use in Test Analysis
- Map manual steps to one or more defined flow categories.
- Identify required preconditions and expected transitions before planning code.
- Use flow definitions to derive meaningful assertions and negative-path checks.

## Stable vs Unstable Flow Recording
- Stable flow: core behavior expected across releases; record as baseline.
- Unstable flow: high-change behavior (feature flags, evolving UX, temporary rules); mark with change risk.
- Each recorded flow should include confidence and last validation source when known.

## Update Rules from User Clarification
- User clarifications can update this file only when behavior is explicit and actionable.
- Clarifications that affect repeatable automation logic should be recorded.
- One-off, temporary discussion details must not be stored as stable flows.
- When clarification conflicts with code, treat as `pending validation` until verified.
