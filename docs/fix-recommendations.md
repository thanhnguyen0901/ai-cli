# Fix Recommendations

## Priority: High

### 1. Add workflow mapping for menu option 3
- Affected file(s): `main-menu.md`, `workflows/` (new or mapped workflow definition)
- Problem: Menu includes `3. Review Existing Automation Code` but no explicit workflow/state artifact defines execution behavior.
- Why it matters: Dry-run can fail or branch ambiguously when user selects option 3.
- Recommended fix: Add a dedicated workflow file (for example `workflows/review-automation-code.md`) or explicitly map option 3 to an existing workflow with state/output contract.

### 2. Reconcile state model between rules and workflow artifacts
- Affected file(s): `rules/workflow-rules.md`, `workflows/generate-test.md`, `workflows/approve-generate.md`, optionally a new `workflows/solution-review.md`
- Problem: Rules require separate `ANALYZE`, `SOLUTION REVIEW`, `APPROVE`, `GENERATE` states, but workflows combine some states and use different naming (`ANALYZE TEST`, `APPROVE -> GENERATE`).
- Why it matters: State-driven orchestration logic can be inconsistent in dry-run or future implementation.
- Recommended fix: Either split workflows to match rule states exactly or update rules to reflect intentional combined-state model.

## Priority: Medium

### 3. Standardize workflow output contracts with global response contract
- Affected file(s): `rules/global-rules.md`, all `workflows/*.md`
- Problem: Global required response fields (`Inputs Used`, `Findings`, `Reuse Candidates`) are not consistently listed in workflow output contracts.
- Why it matters: Output inconsistency reduces determinism and auditability.
- Recommended fix: Add a common minimum response contract block in each workflow file.

### 4. Clarify startup ownership boundary
- Affected file(s): `start.md`, `workflows/setup-project.md`
- Problem: Both documents define overlapping startup responsibilities.
- Why it matters: Can create implementation ambiguity when wiring orchestrator behavior.
- Recommended fix: Define `start.md` as trigger contract and `setup-project.md` as executable startup state owner, with explicit handoff line.

### 5. Tighten update-context to explicitly include context-rules required fields
- Affected file(s): `workflows/update-context.md`, `rules/context-rules.md`
- Problem: Workflow references template use, but required fields from `context-rules.md` are not explicitly enforced in workflow output contract.
- Why it matters: Risk of incomplete context/memory updates in future runs.
- Recommended fix: Add mandatory field checklist (`Date`, `Source Files`, `Change Summary`, `Impact on Generation`, `Confidence`) to update-context workflow.

## Priority: Low

### 6. Add explicit fallback behavior for unsupported menu selections by name
- Affected file(s): `main-menu.md`
- Problem: Invalid numeric input handling exists, but no explicit behavior for text aliases.
- Why it matters: Minor usability/determinism issue.
- Recommended fix: Define that non-numeric input is invalid unless exact alias mapping is introduced.

### 7. Add optional quick-reference links between related docs
- Affected file(s): `start.md`, `main-menu.md`, `workflows/*.md`, `templates/*.md`
- Problem: Cross-file navigation is implicit.
- Why it matters: Minor maintainability/readability improvement.
- Recommended fix: Add short “Related Files” blocks in each workflow.
