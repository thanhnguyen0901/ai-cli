# Custom Commands Context

## Purpose
- Track real custom command and shared extension APIs available to automation code.
- Prevent AI-CLI from inventing non-existent commands/helpers during generation.

## Framework-Specific Command Surfaces
- Cypress:
  - custom commands in support layer (for example `cypress/support/commands.*`),
  - potential command overwrite patterns,
  - command chaining conventions.
- Playwright:
  - fixture extensions,
  - shared helper wrappers,
  - custom test utilities that act as command equivalents.

## Learning and Documentation Rules
- During codebase learning, inspect command/fixture/helper extension points first.
- For each discovered command-equivalent, record:
  - `Name`
  - `Framework`
  - `Source File`
  - `Arguments`
  - `Behavior Summary`
  - `Typical Usage`
  - `Known Constraints`
- Mark uncertain command behavior as `unverified` until code usage is confirmed.

## Impact on Test Generation
- Generation must prefer existing commands/extensions for repeated workflows.
- If command exists, align with its expected signature and side effects.
- If command is missing, do not fabricate it; either use lower-level actions or propose explicit new abstraction through approval path.

## Risk Controls
- Inventing missing commands is prohibited.
- Assuming command behavior without code evidence is prohibited.
- Outdated command documentation must be corrected when conflicts are discovered.

## Source of Truth Policy
- Only commands/helpers found in codebase are considered available.
- Context notes are supportive; observed code definitions and usage win on conflict.
