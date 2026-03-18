# Automation Style Guide Memory

## Purpose
- Capture real style conventions observed in the repository for consistent generation and review.
- Reflect actual code practices, not preferred theory.

## Style Record Schema
- `Style Area`:
- `Observed Convention`:
- `Evidence Source`:
- `Framework Scope`: (`cypress` | `playwright` | `shared`)
- `Confidence`: (`high` | `medium` | `low`)
- `Last Validated`:

## Required Style Areas
- Naming conventions (functions, classes, test names).
- File naming patterns.
- Abstraction preferences (helpers/page objects/fixtures usage depth).
- Page object usage style.
- Helper usage style.
- Assertion style.
- Selector usage tendencies.
- Mocking/intercept style.

## Usage During Generation and Review
- Generation must align with dominant observed style before introducing new patterns.
- Review must flag style drift that increases maintenance cost.
- If style varies by module, follow local convention in target module.

## Refresh Rules
- Revalidate style records during learn/rescan and after large code additions.
- Deprecate outdated style records when codebase standards evolve.
- Keep confidence tied to recency and coverage of sampled code.
