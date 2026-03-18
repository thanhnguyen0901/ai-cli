# Project Summary Memory

## Purpose
- Maintain an evolving, high-signal summary of the current automation repository.
- Provide fast operational context for planning and generation without replacing codebase verification.

## Summary Snapshot Format
- `Last Updated`:
- `Update Source`: (`learn` | `rescan` | `generation` | `manual clarification`)
- `Confidence`: (`high` | `medium` | `low`)

## Required Summary Fields
- `Primary Framework(s)`:
  - detected framework mode (`cypress`, `playwright`, `hybrid`),
  - framework boundary notes.
- `Primary Language`:
  - dominant language (`javascript`, `typescript`, mixed).
- `Repository Organization`:
  - top-level automation layout and dominant folder strategy.
- `Automation Maturity`:
  - baseline maturity statement (coverage shape, reuse depth, consistency level).
- `Major Reusable Assets`:
  - key helpers/page objects/commands/fixtures currently relied upon.
- `Major Known Risks`:
  - high-impact reliability and maintainability risks.
- `Important Business Areas Covered`:
  - major domains/workflows with existing automation evidence.

## Refresh Rules
- Refresh after every significant learn/rescan cycle.
- Refresh when generation introduces meaningful reusable assets or architecture changes.
- Refresh when user-approved clarifications materially change business behavior interpretation.

## Staleness Controls
- Mark stale sections explicitly if not recently validated.
- Downgrade confidence when architecture or conventions changed without full rescan.
- Do not preserve contradicted facts; replace with code-evidenced updates.

## Source of Truth Policy
- This summary is operational memory, not authority.
- Codebase facts override summary entries on conflict.
