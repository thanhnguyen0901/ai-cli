# Current Gaps Memory

## Purpose
- Track confirmed and suspected automation gaps that affect planning quality and generation safety.
- Prioritize improvements that reduce duplication, flakiness, and inconsistency.

## Gap Categories
- Missing page objects or equivalent abstractions.
- Missing reusable helpers.
- Weak selector coverage.
- Duplicated logic.
- Flaky areas.
- Missing coverage patterns.
- Framework inconsistencies.

## Gap Entry Schema
- `Gap ID`:
- `Category`:
- `Description`:
- `Affected Area/Files`:
- `Impact`:
- `Status`: (`confirmed` | `suspected` | `resolved`)
- `Evidence Source`:
- `Recommended Action`:
- `Last Reviewed`:

## Planning Usage Rules
- Treat `confirmed` gaps as actionable constraints during solution planning.
- Treat `suspected` gaps as risks requiring validation before structural changes.
- Use gaps to justify reuse extensions or controlled new abstractions.

## Refresh Rules
- Re-evaluate gaps after codebase learning, user clarifications, and code generation.
- Promote/demote status based on verified evidence.
- Close gaps only when code changes are validated in relevant paths.
