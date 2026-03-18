# Playwright Review Checklist

## Readability and Intent
- [ ] Test titles clearly state behavior and expected result.
- [ ] Test flow is organized (arrange -> act -> assert).
- [ ] Assertions validate business-relevant outcomes.

## Locator and Assertion Quality
- [ ] Locators are stable (`getByRole`, `getByLabel`, `getByTestId`, or repo standard).
- [ ] No brittle locator patterns unless justified by DOM constraints.
- [ ] Assertions use `expect` with meaningful matcher choice.

## Async/Await Correctness
- [ ] All async Playwright actions/assertions are properly awaited.
- [ ] No unnecessary `waitForTimeout` where deterministic waits exist.
- [ ] Waits are tied to events, responses, URL, or locator states.

## Fixture and Reuse Discipline
- [ ] Existing fixtures/helpers/page objects are reused where possible.
- [ ] New fixtures/abstractions are justified and scoped.
- [ ] No duplicate reusable layer introduced.

## Maintainability and Fit
- [ ] File placement and naming follow repo structure/style.
- [ ] Changes are minimal and limited to approved scope.
- [ ] Cross-file impact and regression risk are considered.
