# Playwright Structure Guide

## Common Project Layout
- Typical locations (may vary by repo):
  - Tests: `tests/` or `e2e/`
  - Fixtures: `tests/fixtures/` or `fixtures/`
  - Page objects: `tests/page-objects/` or `pages/`
  - Helpers/utils: `tests/helpers/`, `tests/utils/`, or `src/test-utils/`
  - Test data: `tests/data/` or fixture modules
  - Config: `playwright.config.(ts|js)`

## Naming Conventions
- Test files: `*.spec.ts` or project convention.
- Page object files: `<feature>.page.ts` or `<feature>.po.ts`.
- Fixture modules: `<domain>.fixture.ts` or `fixtures.ts`.
- Utility modules: action-oriented names (`auth-helper.ts`, `cart-utils.ts`).

## Separation Guidance
- Keep test scenarios in spec files.
- Keep cross-test environment setup in fixtures.
- Keep UI interaction encapsulation in page objects where pattern exists.
- Keep domain-independent helpers in utils.
- Avoid embedding large reusable logic directly in specs.

## Generation Interpretation Rules
- Detect existing repo pattern first; follow it rather than imposing a new structure.
- Reuse existing fixtures/page objects/helpers before creating new files.
- Place new artifacts near related tests/features to preserve locality.
- If mixed conventions exist, choose the dominant convention in the targeted module.

## Maintainability Expectations
- Tests should remain readable without opening many indirection layers.
- Shared abstractions should reduce duplication, not hide intent.
- Config-driven behavior (projects, retries, timeouts) should be respected during generation.
