# Repo Architecture Context

## Purpose
- Define how automation repository structure is documented for AI-CLI learning, planning, generation, and review.
- Provide a stable architecture schema that can be enriched with real repository findings.

## Architecture Documentation Model
- Capture architecture by capability area and physical location.
- Record both directory conventions and framework-specific deviations.
- Maintain explicit evidence references to actual files when learned.

## Required Areas to Capture
- Test folders:
  - primary spec/test directories,
  - framework split (`cypress`, `playwright`, or hybrid separation),
  - naming conventions for test files.
- Support/setup:
  - global setup hooks,
  - shared bootstrap logic,
  - framework initialization points.
- Fixtures and test data:
  - static fixtures,
  - generated test data builders,
  - environment-specific data sources.
- Page objects:
  - location and naming convention,
  - abstraction boundaries.
- Helpers/utils:
  - shared utility modules,
  - helper ownership by feature/domain.
- Config files:
  - framework config,
  - project-level test config,
  - environment settings integration points.
- Shared assertions:
  - assertion helper modules,
  - matcher extensions or wrapper APIs.

## Interpretation Rules for AI-CLI
- During learning:
  - detect dominant architecture pattern before proposing changes,
  - record framework boundaries and cross-layer dependencies,
  - flag mixed patterns that increase maintenance risk.
- During generation:
  - follow existing directory and naming conventions,
  - prefer extending existing modules over introducing new structure,
  - keep changes local to the target feature area.

## Update Rules After Codebase Scanning
- Add verified paths and patterns under each required area.
- Include evidence references for each architecture statement.
- Mark uncertain architecture elements as `unverified` until confirmed.
- Remove stale notes that conflict with observed code.

## Source of Truth Policy
- Actual codebase structure is authoritative.
- If this document conflicts with current code, the codebase wins.
- Conflicts must trigger context correction in the next update cycle.
