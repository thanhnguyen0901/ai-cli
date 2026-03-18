# Business Domain Map Memory

## Purpose
- Preserve project-specific business understanding discovered from code and approved clarifications.
- Support scenario interpretation, expected behavior validation, and risk-aware test planning.

## Domain Record Schema
- `Module/Domain`:
- `Key Entities`:
- `User Roles`:
- `Primary Workflows`:
- `Automation-Relevant Business Rules`:
- `Evidence Source`:
- `Confidence`: (`high` | `medium` | `low`)
- `Last Validated`:

## Required Categories
- Major modules.
- Key entities.
- User roles/permissions.
- Important workflows.
- Business rules affecting automation outcomes.

## Difference from Stable Business Flow Context
- `context/business-flows.md` defines stable taxonomy and policy-level flow structure.
- This file stores project-specific, evolving domain details discovered over time.

## Update Rules
- Update after codebase learning that reveals domain semantics.
- Update after user clarification that changes repeatable behavior expectations.
- Mark conflicting interpretations as `pending validation` until code-confirmed.

## Fact Quality Rules
- Uncertain assumptions must never be stored as facts.
- Low-confidence entries must include explicit follow-up validation action.
- One-off temporary notes should remain outside durable domain records.
