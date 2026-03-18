# Cypress Review Checklist

## Readability and Intent
- [ ] Test name describes business behavior and expected outcome.
- [ ] Test flow is easy to follow (arrange -> act -> assert).
- [ ] Assertions are tied to meaningful business outcomes.

## Cypress-Specific Correctness
- [ ] Commands rely on Cypress retryability instead of manual sleeps.
- [ ] No unnecessary `cy.wait(ms)` when deterministic signals exist.
- [ ] `cy.intercept()` is registered before triggering requests.
- [ ] `cy.wait('@alias')` is used where API completion drives UI state.

## Selector Quality
- [ ] Selectors are stable and consistent with repo strategy.
- [ ] No brittle deep CSS chains or fragile index-only selectors.
- [ ] Scoped querying is used where duplicate elements exist.

## Reuse and Duplication
- [ ] Existing commands/helpers/page objects were reused where possible.
- [ ] No duplicate abstractions were introduced.
- [ ] Repeated setup/actions are extracted appropriately.

## Assertions and Reliability
- [ ] Assertions are explicit (`be.visible`, `contain`, `have.text`, etc.).
- [ ] Positive and critical negative states are validated when relevant.
- [ ] Async behavior is synchronized with observable signals.

## Maintainability and Fit
- [ ] Changes follow repo structure and naming conventions.
- [ ] New files are justified and correctly placed.
- [ ] Code remains minimal and scoped to requested task.
