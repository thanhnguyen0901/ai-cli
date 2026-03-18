# Cypress Commands Guide

## Action Mapping

### Visit Page
```js
cy.visit('/orders')
```

### Click
```js
cy.get('[data-testid="submit-order"]').click()
```

### Type Input
```js
cy.get('[data-testid="email"]').clear().type('user@example.com')
```

### Select Dropdown
```js
cy.get('[data-testid="country"]').select('United States')
```

### Checkbox and Radio
```js
cy.get('[data-testid="terms"]').check()
cy.get('[name="plan"][value="pro"]').check()
```

### File Upload
```js
cy.get('input[type="file"]').selectFile('cypress/fixtures/avatar.png')
```

### Intercept API
```js
cy.intercept('GET', '**/api/orders*').as('getOrders')
```

### Wait for API
```js
cy.wait('@getOrders').its('response.statusCode').should('eq', 200)
```

### Assert Text, Visibility, Existence
```js
cy.get('[data-testid="toast"]').should('contain', 'Saved')
cy.get('[data-testid="summary"]').should('be.visible')
cy.get('[data-testid="row-123"]').should('exist')
```

### Handle Modal
```js
cy.get('[data-testid="open-modal"]').click()
cy.get('[role="dialog"]').should('be.visible')
cy.get('[data-testid="confirm"]').click()
```

### Navigation Assertion
```js
cy.url().should('include', '/checkout')
cy.go('back')
```

## Selector Guidance
- Start with repository-preferred selectors (`data-testid` or established pattern).
- Scope queries when needed to avoid collisions:
```js
cy.get('[data-testid="cart"]').within(() => {
  cy.contains('button', 'Checkout').click()
})
```
- Use text queries carefully; prefer unique text tied to business meaning.

## Async and Retryability Notes
- Cypress retries `cy.get()` and `.should(...)` automatically until timeout.
- Prefer retryable assertions over manual polling.
- Avoid `cy.wait(ms)` unless there is no observable app signal.
- Chain commands; do not mix Cypress chain flow with unmanaged async logic.
