# Playwright Patterns

## Mental Model
- Playwright uses explicit async/await with browser contexts and pages.
- Locators are first-class and should drive interaction and assertion strategy.
- Tests should be isolated via fixtures/context to ensure reproducibility.

## Preferred Test Shape
- Use `test.describe` to group related behavior.
- Use `test(...)` for scenario-level validation.
- Keep a clean flow:
  1. Arrange (fixture setup, route mocks, test data)
  2. Act (locator-driven interactions)
  3. Assert (`expect` on locators, URL, and network outcomes)

## Fixtures and Page Usage
- Use built-in fixtures (`page`, `context`, `request`) and project fixtures for shared setup.
- Keep fixture setup deterministic and scoped.
- Prefer project fixture patterns over ad hoc per-test bootstrapping.

## Locator-First Guidance
- Prefer `page.getByRole`, `page.getByLabel`, `page.getByTestId` when available.
- Keep locators resilient and business-meaningful.
- Reuse locator definitions from existing page objects/helpers where established.

## Page Object and Helper Usage
- Use page objects/helpers for reusable interaction sequences.
- Keep page objects focused on actions and element state access.
- Keep business assertions primarily in test files unless repo convention differs.

## Assertion Style
- Use `await expect(locator)...` for UI assertions.
- Prefer semantic assertions (`toBeVisible`, `toHaveText`, `toHaveURL`, `toBeEnabled`).
- Assert key outcomes immediately after the action that should produce them.

## Setup and Teardown
- Use `test.beforeEach` for per-test navigation/state setup.
- Use `test.beforeAll` only when safe and truly shared.
- Use cleanup logic only when the suite requires explicit teardown.

## Anti-Patterns to Avoid
- Missing `await` on async Playwright calls.
- Using brittle raw selectors when role/test-id locators exist.
- Hard-coded sleeps (`waitForTimeout`) for normal synchronization.
- Mixing too many business flows into one test.
- Creating new abstractions when existing fixtures/helpers already solve the need.
