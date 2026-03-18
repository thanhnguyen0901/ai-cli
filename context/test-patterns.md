# Test Patterns Context

## Purpose
- Define stable testing patterns that guide consistent, reviewable automation output across Cypress and Playwright.
- Separate high-level test intent from reusable implementation details.

## Core Philosophy
- Reuse-first: prefer existing helpers, page objects, commands, fixtures, and utilities.
- Intent-first specs: keep business scenario meaning clear in tests.
- Minimize abstraction noise: extract only repeated, durable behavior.

## Pattern Standards

### Setup
- Use standardized hooks/fixtures for repeatable preconditions.
- Keep setup deterministic and scoped per scenario unless shared setup is explicitly safe.

### Actions
- Represent user actions in readable, domain-aligned steps.
- Use reusable wrappers for repeated low-level UI interactions.

### Assertions
- Assert business outcomes, not incidental implementation details.
- Keep primary assertions close to triggering actions.
- Include negative/error assertions when flow behavior depends on validation.

### Data Preparation
- Prefer fixtures/builders for predictable test data.
- Avoid hard-coded mutable environment dependencies.

### Network Mocking
- Mock only where determinism or isolation requires it.
- Keep mocks minimal and aligned with scenario intent.
- Validate critical request/response behavior when relevant.

### Wait Handling
- Prefer observable signals (UI state, URL, network completion, locator state).
- Avoid arbitrary fixed sleeps unless no deterministic signal exists.

## Separation of Intent vs Reusable Implementation
- Test files should express scenario and expectation.
- Shared modules should encapsulate repeated mechanics.
- Do not hide business assertions inside opaque helper layers unless repository convention requires it.

## Anti-Patterns to Avoid
- Multi-flow tests that combine unrelated business behavior.
- Repeated setup/actions copied across specs.
- Hidden assumptions about selectors, timing, or permissions.
- Creating new abstractions when equivalent reusable assets already exist.

## Post-Learning Enrichment Rules
- Add discovered repository-specific patterns under each standard category.
- Record framework-specific deviations only when actually present.
- Mark deprecated patterns and migration direction when identified.
