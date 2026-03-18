# Codebase Index Memory

## Purpose
- Maintain an evolving index of high-value code locations to reduce repeated full-repo scans.
- Enable faster navigation for analysis, planning, generation, and review tasks.

## Index Entry Schema
- `Area Type`: (`directory` | `file` | `module`)
- `Path`:
- `Role`:
- `Framework Scope`: (`cypress` | `playwright` | `shared`)
- `Last Validated`:
- `Confidence`: (`high` | `medium` | `low`)
- `Notes`:

## Required Index Sections
- Important directories.
- Key files.
- Page objects / equivalent abstractions.
- Helpers and utilities.
- Fixtures and test data.
- Shared assertions/matchers.
- Config locations.
- Framework-specific hotspots (Cypress and Playwright).

## Operational Usage Rules
- Use this index first for targeted lookup before deep repo scans.
- Prefer indexed hotspots when mapping manual steps to implementation points.
- If index confidence is low, validate against code before making decisions.

## Refresh Rules
- Refresh entries after learn/rescan and after generation touching indexed paths.
- Remove or relabel entries that no longer exist or changed role.
- Upgrade confidence only after direct code validation.

## Conflict and Source-of-Truth Policy
- Codebase overrides outdated index entries.
- Conflicting index entries must be corrected immediately in memory update cycle.
