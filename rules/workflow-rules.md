# Workflow Rules

## Mandatory State Machine
- The workflow must follow this logical state order:
  - `START -> SETUP -> LEARN -> READY -> ANALYZE -> SOLUTION REVIEW -> DISCUSS/EXPLAIN -> APPROVE -> GENERATE -> CONTEXT UPDATE`
- The system uses an intentional combined-state workflow artifact model:
  - `workflows/generate-test.md` implements `ANALYZE + SOLUTION REVIEW`.
  - `workflows/approve-generate.md` implements `APPROVE + GENERATE` with an internal hard gate.
- Combined-state artifacts are valid only when required state order and gating are preserved.
- States may loop only where explicitly allowed.
- The assistant must always declare the current logical state in responses.

## State Definitions and Required Actions

### START
- Initialize AI-CLI mode.
- Confirm controlled workflow operation.
- Do not analyze or generate code in this state.

### SETUP
- Load AI-CLI local assets: `rules/`, `workflows/`, `frameworks/`, `context/`, `memory/`.
- Confirm framework target (Cypress or Playwright) if not already explicit.
- Ask whether to run codebase learning.

### LEARN
- Trigger only after user approval.
- Scan repository structure, automation patterns, helpers, selectors, commands, page objects, and naming conventions.
- Update internal understanding using verifiable code evidence.
- Prepare updates for context and memory artifacts.

### READY
- Report learning completion and known constraints.
- Confirm readiness for test request intake.
- Do not generate code yet.
- READY state supports a deterministic inline behavior for menu option `5`:
  - `Explain Current Project Understanding` executes as a READY inline action (no separate workflow artifact/state transition).
  - Inputs are synthesized from `context/` and `memory/` with codebase-as-source-of-truth constraints.

### ANALYZE + SOLUTION REVIEW (Combined Artifact Allowed)
- Parse requested test scenario and expected behavior.
- Map steps to existing codebase capabilities.
- Identify missing information, risks, and ambiguity.
- Propose implementation plan before coding.
- Distinguish reusable components from required new code.
- List impacted files and expected change scope.
- Ask for next route: discuss, explain, or approve.

### DISCUSS/EXPLAIN
- `DISCUSS`: iterate on plan based on user feedback.
- `EXPLAIN`: provide precise rationale for design choices and tradeoffs.
- Loop between solution review point and `DISCUSS/EXPLAIN` is allowed until user confirms plan maturity.
- No code generation in this state.

### APPROVE + GENERATE (Combined Artifact Allowed)
- Require explicit user approval before entering generation segment.
- Approval must be unambiguous (for example: "approved", "proceed", "generate now").
- If approval is absent, vague, or conditional, remain in pre-generation states.
- Execute code generation only after approval gate passes.
- Apply minimal, framework-correct, convention-aligned changes.
- Clearly report modified files and newly created files.

### CONTEXT UPDATE
- Update project context/memory artifacts with durable learnings from generated changes.
- Record decisions, reusable patterns, and known limitations.
- Do not store speculative or temporary discussion artifacts.

## Non-Skippable Rules
- The assistant must not skip mandatory logical states.
- The assistant must not jump from `ANALYZE` directly to `GENERATE`.
- The assistant must not bypass approval gate behavior.
- The assistant must not output final code before solution review is accepted.

## Invalid Behaviors
- Generating code in `START`, `SETUP`, `LEARN`, `READY`, `ANALYZE`, `SOLUTION REVIEW`, or `DISCUSS/EXPLAIN`.
- Entering generation segment of combined `APPROVE + GENERATE` workflow without explicit approval.
- Treating implicit enthusiasm as approval.
- Ignoring unresolved ambiguities and fabricating details.
- Modifying unrelated files during `GENERATE`.

## Approval Gate Enforcement
- A hard gate exists between approval and generation segments, including inside combined-state artifact workflows.
- If the gate fails, assistant action is limited to clarification, discussion, or analysis.
- The assistant must restate what is waiting for approval when blocked.

## Shared Workflow Output Contract
- Every workflow response must include this minimum contract:
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
- If a field does not apply in a specific workflow response, it must be returned as `N/A`.
