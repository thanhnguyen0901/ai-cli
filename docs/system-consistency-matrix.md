# System Consistency Matrix

## 1. Rule -> Workflow Governance Matrix

| Rule File | Governed Workflows | Enforcement Notes |
|---|---|---|
| `rules/global-rules.md` | All workflows | Defines AI-CLI identity, anti-hallucination, structured responses, reuse-first, no free-chat behavior |
| `rules/workflow-rules.md` | `setup-project`, `learn-codebase`, `generate-test`, `discuss-solution`, `explain-solution`, `approve-generate`, `update-context` | Defines canonical state machine and gating; currently stricter than workflow artifact granularity |
| `rules/context-rules.md` | `learn-codebase`, `update-context`, post-generation memory updates | Defines context vs memory, freshness checks, conflict resolution, persistence policy |
| `rules/code-generation-rules.md` | `approve-generate` and any generation step | Defines explicit approval precondition, reuse-first implementation, style/scope constraints |

## 2. Workflow -> Template Support Matrix

| Workflow | Template(s) Used | Coverage |
|---|---|---|
| `workflows/generate-test.md` | `templates/test-analysis-template.md`, `templates/solution-plan-template.md` | Analysis and pre-generation solution proposal |
| `workflows/approve-generate.md` | `templates/codegen-checklist-template.md` | Pre-generation gate/checklist enforcement |
| `workflows/update-context.md` | `templates/context-update-template.md` | Structured context/memory update record |
| `workflows/discuss-solution.md` | (Indirect) `solution-plan-template` | Proposal delta updates and return to review options |
| `workflows/explain-solution.md` | (Indirect) `solution-plan-template` | Expanded rationale over current proposal |

## 3. Workflow -> Context/Memory Update Matrix

| Workflow | Context Files Impacted | Memory Files Impacted | Notes |
|---|---|---|---|
| `setup-project` | Read-only status checks | Read-only status checks | Reports presence/freshness risk |
| `learn-codebase` | `context/*` (architecture, selectors, patterns, risks, etc.) | `memory/*` (summary, index, maps, style, history anchors) | Primary enrichment workflow |
| `generate-test` | No direct write required | No direct write required | Produces analysis/plan artifacts pre-approval |
| `discuss-solution` | Optional queued update via update-context | Optional queued update via update-context | Clarification persistence gate |
| `explain-solution` | Typically none direct | Typically none direct | Returns to review options |
| `approve-generate` | Optional post-generation update prompt | Optional post-generation update prompt | Handoff to update-context |
| `update-context` | Direct structured updates | Direct structured updates | Conflict-aware persistence owner |

## 4. Framework Guide -> Generation/Review Path Matrix

| Framework Guides | Used In Generation | Used In Review | Notes |
|---|---|---|---|
| `frameworks/cypress/patterns.md` | Yes | Yes | Cypress mental model and anti-pattern controls |
| `frameworks/cypress/commands.md` | Yes | Yes | Action-to-command mapping and retry guidance |
| `frameworks/cypress/structure.md` | Yes | Yes | Placement and naming interpretation |
| `frameworks/cypress/review-checklist.md` | Indirect | Yes | Quality gate for Cypress output |
| `frameworks/playwright/patterns.md` | Yes | Yes | Locator-first async model and anti-pattern controls |
| `frameworks/playwright/commands.md` | Yes | Yes | Action-to-command mapping and async correctness |
| `frameworks/playwright/structure.md` | Yes | Yes | Placement and naming interpretation |
| `frameworks/playwright/review-checklist.md` | Indirect | Yes | Quality gate for Playwright output |

## 5. Entry and Control Flow Matrix

| Layer | Primary File(s) | Role |
|---|---|---|
| Entry trigger | `start.md` | Defines `START` bootstrap contract and readiness response |
| Runtime config | `config.md` | Defines configurable system behavior and safe defaults |
| Menu control | `main-menu.md` | Defines explicit option-based operation and return-to-menu loop |
| State engine | `workflows/*.md` + `rules/workflow-rules.md` | Defines state transitions, guards, and lifecycle behavior |
