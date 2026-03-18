# Cypress Patterns

## Mental Model
- Cypress runs inside the browser and queues commands; commands are asynchronous and retried automatically for many assertions and DOM queries.
- Prefer deterministic UI flows with observable signals (URL, element state, network alias resolution).
- Treat each test as isolated; avoid hidden inter-test dependencies.

## Preferred Test Shape
- Use `describe` to group behavior by feature or business flow.
- Use `it` for one verifiable scenario each.
- Follow a clear sequence inside each test:
  1. Arrange (setup, stubs, data)
  2. Act (user interactions)
  3. Assert (outcomes)
- Keep assertions near the behavior they validate.

## Setup and Hooks
- Use `before` for expensive one-time setup that is safe to share.
- Use `beforeEach` for per-test setup (auth state, seed data, route stubs, initial visit).
- Do not mutate shared state in ways that make tests order-dependent.

## Network and Intercept Patterns
- Register `cy.intercept()` before the action that triggers the request.
- Alias important requests with `.as('<name>')` and wait using `cy.wait('@name')`.
- Assert both UI outcome and relevant response details when behavior depends on API data.
- Stub only what is needed for determinism; do not over-stub the entire app flow.

## Custom Commands and Reusable Helpers
- Prefer existing custom commands for repeated interactions (login, navigation, stable component actions).
- Keep custom commands focused and composable.
- Use page objects/helpers only when they reduce duplication and keep intent readable.
- Avoid creating new abstractions if an existing helper already matches behavior.

## Assertion Style
- Use explicit assertions with meaningful expectations (`contain`, `have.text`, `be.visible`, `have.attr`).
- Assert stable outcomes (URL, data-testid content, API-driven UI state), not incidental styling.
- Keep one primary assertion target per step; add secondary assertions only when they prove business correctness.

## Selector Guidance
- Prefer stable selectors: `data-testid`, semantic roles (when wrapped), durable attributes.
- Avoid brittle selectors: deep CSS chains, index-only selectors, volatile text-only selectors.
- Keep selector strategy aligned with repository conventions.

## Anti-Patterns to Avoid
- Arbitrary `cy.wait(<ms>)` for synchronization when a real signal exists.
- Multiple unrelated business flows in one `it` block.
- Repeating login/setup logic across specs instead of reusing commands/helpers.
- Assertions disconnected from business expectations.
- Introducing new page objects/helpers without proving reuse need.
