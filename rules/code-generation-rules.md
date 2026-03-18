# Code Generation Rules

## Hard Preconditions
- Code generation is forbidden until explicit approval is granted in `APPROVE` state.
- If approval is missing, ambiguous, or revoked, generation must stop immediately.
- If required information is missing, return to workflow clarification; do not fabricate code.

## Reuse-First Implementation Policy
- Reuse existing helpers, page objects, fixtures, custom commands, and utilities first.
- Search for equivalent abstractions before adding new code.
- Duplicate abstractions are prohibited.
- New abstractions require explicit justification tied to unmet reuse needs.

## Architecture and Naming Compliance
- Respect existing repository architecture, directory boundaries, and ownership patterns.
- Follow established naming conventions for files, classes, functions, commands, and selectors.
- Preserve test organization strategy already used by the project.
- Do not introduce cross-layer coupling that violates current design.

## Framework-Specific Correctness
- Cypress output must follow Cypress APIs and project Cypress patterns.
- Playwright output must follow Playwright APIs and project Playwright patterns.
- Never mix framework primitives unless repository design explicitly supports it.
- If target framework is unclear, stop and request clarification in workflow mode.

## Change Scope and Traceability
- Make minimal necessary changes to satisfy approved scope.
- Avoid unrelated refactors during generation.
- Explicitly report:
  - modified files,
  - new files,
  - removed code (if any and approved).
- Keep edits reviewable and localized.

## Style and Consistency
- Match repository code style, linting rules, and formatting conventions.
- Keep behavior explicit; avoid hidden side effects.
- Use existing assertion patterns and waiting/synchronization practices.
- Maintain readability and maintainability standards used in the codebase.

## Selector and Flow Robustness
- Prefer stable selectors and existing selector strategy.
- Avoid brittle selectors (for example: deep CSS chains, volatile text, unstable indices) unless no alternative exists.
- Do not assume business flow branching not present in code evidence.
- If selector or business flow is unclear, stop and ask clarification instead of inventing logic.

## Safety Controls
- Do not edit unrelated files.
- Do not change repository structure without explicit approval.
- Do not introduce secrets, credentials, or environment-specific hardcoding.
- Ensure generated code is consistent with existing test data and environment handling patterns.

## Output Contract for Generation Step
- For each generation action, provide:
  - `Approved Scope`
  - `Reused Components`
  - `New Components`
  - `Files Modified`
  - `Files Created`
  - `Open Risks/Follow-ups`
