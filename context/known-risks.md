# Known Risks Context

## Purpose
- Capture recurring automation risks that must be considered explicitly during analysis, planning, generation, and review.
- Make risk handling a visible planning input, not an implicit assumption.

## Risk Categories
- Flaky selectors:
  - unstable attributes,
  - layout-coupled selectors,
  - volatile text dependencies.
- Async timing issues:
  - race conditions,
  - premature assertions,
  - missing deterministic waits.
- Unstable test data:
  - mutable shared data,
  - non-idempotent setup,
  - environment drift.
- Environment dependency:
  - config-specific behavior,
  - feature flag variance,
  - CI vs local mismatch.
- Auth/session dependency:
  - token/session expiry,
  - cached state leakage,
  - role bootstrap inconsistencies.
- Permission/role variance:
  - role-specific UI divergence,
  - access-denied branches,
  - hidden action states.
- Dynamic UI behavior:
  - delayed rendering,
  - virtualization/infinite scroll,
  - transient overlays/modals.
- Backend latency/network dependency:
  - slow or intermittent API responses,
  - eventual consistency delays,
  - partial failure handling.

## How AI-CLI Uses This File
- Analysis:
  - identify risk categories relevant to requested scenario.
- Solution planning:
  - include mitigation strategy for each applicable risk.
- Review:
  - verify generated code addresses identified risks and avoids brittle assumptions.

## Risk Recording Rules
- Add newly discovered risks from:
  - codebase learning,
  - user clarifications,
  - review findings.
- For each risk entry, record:
  - `Risk Description`
  - `Affected Area`
  - `Impact`
  - `Mitigation Strategy`
  - `Confidence`
  - `Last Validation Source`

## Guardrails
- Risks must be explicit in plans when applicable.
- Do not hide unresolved risks behind optimistic assumptions.
- Do not persist speculative risks without evidence or clear rationale.
