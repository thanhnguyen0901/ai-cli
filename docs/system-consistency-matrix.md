# System Consistency Matrix

## 1) Rules -> Workflows

| Rule | Governed Areas | Consistency Status |
|---|---|---|
| `rules/global-rules.md` | All workflows | Aligned (canonical shared output contract in place) |
| `rules/workflow-rules.md` | State transitions and combined-state model | Aligned |
| `rules/context-rules.md` | Context/memory update governance | Aligned (required fields + confidence split) |
| `rules/code-generation-rules.md` | Approval/generation behavior | Aligned |

## 2) Menu -> Workflow Handling

| Menu Option | Handling Model | Implementation |
|---|---|---|
| `1. Learn or Refresh Codebase` | Workflow artifact | `workflows/learn-codebase.md` |
| `2. Generate Test From Manual Steps` | Workflow artifact | `workflows/generate-test.md` |
| `3. Review Existing Automation Code` | Workflow artifact | `workflows/review-automation-code.md` |
| `4. Update Project Context/Memory` | Workflow artifact | `workflows/update-context.md` |
| `5. Explain Current Project Understanding` | Deterministic READY inline behavior | Explicitly defined in `main-menu.md` and `rules/workflow-rules.md` |
| `6. Exit` | Menu control action | Explicit in `main-menu.md` |

## 3) Workflows -> Templates

| Workflow | Template Dependencies | Status |
|---|---|---|
| `generate-test` | `test-analysis-template`, `solution-plan-template` | Aligned |
| `approve-generate` | `codegen-checklist-template` | Aligned |
| `update-context` | `context-update-template` | Aligned |
| `review-automation-code` | framework review checklists | Aligned |

## 4) Shared Output Contract Determinism

| Contract Field | Global Rule | Workflow Minimum Contract |
|---|---|---|
| `Workflow Name` | Yes | Yes |
| `Current State` | Yes | Yes |
| `Objective` | Yes | Yes |
| `Inputs Consumed` | Yes | Yes |
| `Analysis Summary` | Yes | Yes |
| `Risks` | Yes | Yes |
| `Proposed Action` | Yes | Yes |
| `Required User Decision` | Yes | Yes |
| `Next Allowed Commands` | Yes | Yes |
| `Context Update Needed` | Yes | Yes |

## 5) Context-Update Governance Field Alignment

| Field | rules/context-rules | workflows/update-context | template/context-update |
|---|---|---|---|
| `Date` | Required | Required | Required |
| `Source Files` | Required | Required | Required |
| `Change Summary` | Required | Required | Required |
| `Impact on Generation` | Required | Required | Required |
| `Update Confidence` | Required | Required | Required |
| `Evidence Confidence` | Optional | Optional | Optional |
