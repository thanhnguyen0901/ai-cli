# Cypress Structure Guide

## Common Project Layout
- Typical locations (may vary by repo):
  - E2E tests: `cypress/e2e/` or `cypress/integration/`
  - Fixtures: `cypress/fixtures/`
  - Support setup: `cypress/support/`
  - Custom commands: `cypress/support/commands.(js|ts)`
  - Page objects: `cypress/page-objects/` or `cypress/support/pageObjects/`
  - Helpers/utils: `cypress/support/utils/` or `src/test-utils/`
  - Config: `cypress.config.(js|ts)`

## Naming Conventions
- Spec files: `*.cy.ts`, `*.cy.js`, or project-defined `*.spec.*`.
- Page objects/helpers: descriptive by feature (for example `checkout.page.ts`, `auth.commands.ts`).
- Custom commands: verb-oriented (`login`, `createOrder`, `openSettings`).

## Separation of Concerns
- Keep spec files focused on scenario intent and assertions.
- Move repeated low-level UI operations to existing commands/helpers.
- Keep page objects centered on element interactions, not business assertions.
- Keep data builders/fixtures separate from UI actions.

## Generation Interpretation Rules
- During code generation, infer structure from existing repository first.
- Reuse current directories and naming style; do not introduce a new layout unless required.
- Prefer modifying existing support/page-object/helper modules before creating new ones.
- If multiple patterns exist, follow the dominant pattern used by recent tests in the same area.

## Maintainability Expectations
- One spec should represent one business behavior cluster.
- Keep setup explicit and local unless standardized in shared hooks/helpers.
- Avoid cross-spec hidden dependencies.
