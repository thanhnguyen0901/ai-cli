# Workflow Rules

## Mandatory State Machine
- The workflow must follow this exact state order:
  - `START -> SETUP -> LEARN -> READY -> ANALYZE -> SOLUTION REVIEW -> DISCUSS/EXPLAIN -> APPROVE -> GENERATE -> CONTEXT UPDATE`
- States may loop only where explicitly allowed.
- The assistant must always declare the current state in responses.

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

### ANALYZE
- Parse requested test scenario and expected behavior.
- Map steps to existing codebase capabilities.
- Identify missing information, risks, and ambiguity.
- Produce a reuse-first technical analysis.

### SOLUTION REVIEW
- Propose implementation plan before coding.
- Distinguish reusable components from required new code.
- List impacted files and expected change scope.
- Ask for discussion or explanation route.

### DISCUSS/EXPLAIN
- `DISCUSS`: iterate on plan based on user feedback.
- `EXPLAIN`: provide precise rationale for design choices and tradeoffs.
- Loop between `SOLUTION REVIEW` and `DISCUSS/EXPLAIN` is allowed until user confirms plan maturity.
- No code generation in this state.

### APPROVE
- Require explicit user approval to generate code.
- Approval must be unambiguous (for example: "approved", "proceed", "generate now").
- If approval is absent, vague, or conditional, remain in pre-generation states.

### GENERATE
- Execute code generation only after approval.
- Apply minimal, framework-correct, convention-aligned changes.
- Clearly report modified files and newly created files.

### CONTEXT UPDATE
- Update project context/memory artifacts with durable learnings from generated changes.
- Record decisions, reusable patterns, and known limitations.
- Do not store speculative or temporary discussion artifacts.

## Non-Skippable Rules
- The assistant must not skip mandatory states.
- The assistant must not jump from `ANALYZE` to `GENERATE`.
- The assistant must not bypass `APPROVE`.
- The assistant must not output final code before solution review is accepted.

## Invalid Behaviors
- Generating code in `START`, `SETUP`, `LEARN`, `READY`, `ANALYZE`, `SOLUTION REVIEW`, or `DISCUSS/EXPLAIN`.
- Treating implicit enthusiasm as approval.
- Ignoring unresolved ambiguities and fabricating details.
- Modifying unrelated files during `GENERATE`.

## Approval Gate Enforcement
- A hard gate exists between `APPROVE` and `GENERATE`.
- If the gate fails, assistant action is limited to clarification, discussion, or analysis.
- The assistant must restate what is waiting for approval when blocked.
