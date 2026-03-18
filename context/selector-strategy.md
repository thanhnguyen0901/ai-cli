# Selector Strategy Context

## Purpose
- Define the official selector policy used by AI-CLI for test generation and code review.
- Ensure selector choices are stable, maintainable, and framework-appropriate.

## Selector Priority Order
1. Explicit stable test selectors (`data-testid`, project-approved test attributes).
2. Accessible semantic selectors (role, label, name) when stable and unique.
3. Durable domain attributes (non-volatile IDs or business keys).
4. Scoped text-based selectors tied to stable business wording.
5. Structural CSS selectors only when no better option exists.

## Recommended Stable Selectors
- Dedicated automation attributes (`data-testid`, `data-cy`, project-specific equivalents).
- Accessibility-driven selectors with consistent semantics.
- Selectors scoped to stable container regions to reduce collisions.

## Discouraged Selectors
- Deep CSS chains tied to layout.
- Index-only selectors (`:nth-child`, positional assumptions) without stability guarantees.
- Volatile text selectors for content likely to change frequently.
- Styling/class selectors that reflect presentation rather than identity.

## Fallback Rules
- If priority-1 selectors are absent:
  - use semantic selectors with strict scoping,
  - document fallback rationale,
  - record risk level.
- If no stable selector exists:
  - pause generation for clarification when risk is high,
  - otherwise use least-brittle fallback and explicitly flag follow-up need.

## Framework-Aware Notes
- Cypress:
  - prefer `cy.get('[data-testid="..."]')` or equivalent repo standard,
  - leverage retryable assertions instead of selector over-complexity.
- Playwright:
  - prefer locator-first APIs (`getByRole`, `getByLabel`, `getByTestId`),
  - use scoped locators and explicit expectations.

## Influence on Generation and Review
- Generation must follow this priority order unless repository convention dictates otherwise.
- Review must flag brittle selector patterns as correctness and maintenance risks.
- Selector decisions must be traceable to repository strategy and target UI behavior.

## Post-Learning Enrichment Rules
- Record repo-specific selector conventions discovered in code.
- Add approved selector helper APIs and wrapper patterns.
- Document known weak-selector zones and recommended alternatives.
