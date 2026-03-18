# Dry-Run Readiness

## Current Readiness Status
- Overall: `READY WITH MINOR FIXES`

## Can START be tested now?
- Yes.
- Reason: `start.md`, `config.md`, `setup-project` workflow, and `main-menu` behavior are defined with explicit load order and yes/no learning prompt.

## Can learn-codebase be tested now?
- Yes.
- Reason: `workflows/learn-codebase.md` defines scan scope, extraction targets, stale-memory handling, and completion reporting.

## Can generate-test be tested now?
- Yes, with caveats.
- Reason: analysis and solution planning templates are integrated; discuss/explain/approve loop exists.
- Caveat: state naming/granularity mismatch with canonical workflow rules may cause orchestration ambiguity.

## What must be fixed first (if anything)?
1. Add or map a workflow for main-menu option 3 (`Review Existing Automation Code`).
2. Align workflow artifacts with canonical state model (`ANALYZE`, `SOLUTION REVIEW`, `APPROVE`, `GENERATE`) or formally update rules to reflect intentional combined states.

## Suggested Dry-Run Order
1. Run `START` flow and verify load-status response sections.
2. Choose `yes` for learn/refresh and validate LEARN completion report sections.
3. Return to menu and run option 2 (`Generate Test From Manual Steps`) with a sample scenario.
4. Validate template-shaped outputs for analysis and solution plan.
5. Exercise discuss loop with selector/business clarifications.
6. Exercise explain loop and confirm no code generation occurs.
7. Provide explicit approval and validate checklist gate behavior.
8. Validate post-generation prompt for context/memory update.
9. Run update-context path and verify structured update fields and conflict handling.

## Practical Dry-Run Pass Criteria
- No code generation before explicit approval.
- Framework choice stays consistent per scenario.
- Outputs remain structured and state-labeled.
- Reuse-first reasoning is visible in proposals.
- Context/memory updates are evidence-based and conflict-aware.
