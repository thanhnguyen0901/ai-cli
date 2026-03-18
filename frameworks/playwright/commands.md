# Playwright Commands Guide

## Action Mapping

### Navigate to Page
```ts
await page.goto('/orders')
```

### Click
```ts
await page.getByTestId('submit-order').click()
```

### Fill Input
```ts
await page.getByTestId('email').fill('user@example.com')
```

### Select Dropdown
```ts
await page.getByTestId('country').selectOption({ label: 'United States' })
```

### Checkbox and Radio
```ts
await page.getByTestId('terms').check()
await page.locator('input[name="plan"][value="pro"]').check()
```

### File Upload
```ts
await page.setInputFiles('input[type="file"]', 'tests/fixtures/avatar.png')
```

### Route/Intercept Network
```ts
await page.route('**/api/orders*', async route => {
  await route.continue()
})
```

### Wait for Response
```ts
const responsePromise = page.waitForResponse(r =>
  r.url().includes('/api/orders') && r.status() === 200
)
await page.getByTestId('refresh-orders').click()
await responsePromise
```

### Assert Text, Visibility, Existence
```ts
await expect(page.getByTestId('toast')).toContainText('Saved')
await expect(page.getByTestId('summary')).toBeVisible()
await expect(page.getByTestId('row-123')).toBeAttached()
```

### Modal/Dialog Handling
```ts
await page.getByTestId('open-modal').click()
await expect(page.getByRole('dialog')).toBeVisible()
await page.getByTestId('confirm').click()
```

### Navigation Assertion
```ts
await expect(page).toHaveURL(/\/checkout/)
await page.goBack()
```

## Locator Guidance
- Prefer role, label, and test-id locators over brittle CSS/XPath.
- Keep locator definitions centralized if the repo uses page objects.
- Scope locators via parent containers when duplicate elements are expected.

## Async/Await Notes
- All Playwright actions/assertions are promise-based; missing `await` is a correctness bug.
- Prefer event/response/locator waits over fixed delays.
- Use `expect` auto-waiting behavior instead of manual polling loops.
