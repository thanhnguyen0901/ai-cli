# Page Object Map Context

## Purpose
- Map pages/screens/modules to automation abstractions so AI-CLI can reuse existing interaction layers consistently.
- Support both projects with full page objects and projects using helper-based alternatives.

## Mapping Model
- Each map entry should capture:
  - `Page/Screen/Module Name`
  - `Automation Abstraction` (page object or helper module)
  - `Source File`
  - `Covered Actions`
  - `Missing Actions`
  - `Selector Strategy Notes`
  - `Reuse Gap Notes`

## Usage in Solution Planning
- During planning, locate relevant map entries before proposing new abstractions.
- Prefer extending mapped abstractions when missing actions are small and coherent.
- If abstraction coverage is weak, call out reuse gap and justify proposed additions.

## Projects Without Full Page Objects
- If project uses helper-driven or direct-locator approach:
  - record equivalent modules as abstraction targets,
  - keep mapping by feature/module instead of strict page-object class names,
  - avoid forcing a new page-object architecture unless explicitly requested.

## Update Triggers
- Add or revise entries after:
  - codebase learning,
  - approved generation that changes abstraction coverage,
  - user clarification introducing durable UI behavior changes.

## Consistency Rules
- Keep action names aligned with existing repository naming.
- Mark stale entries when source files or interfaces change.
- Tie each entry to verifiable code evidence where available.
