# Decisions Log Memory

## Purpose
- Preserve approved clarifications and working decisions that influence future discussions, planning, and generation.
- Keep decision history explicit and traceable.

## Decision Types to Record
- Selector decisions.
- Reuse decisions.
- Architectural decisions.
- Business behavior clarifications.
- Framework-specific preferences.
- File ownership/placement decisions.

## Decision Entry Schema
- `Decision ID`:
- `Date/Session`:
- `Decision`:
- `Reason`:
- `Source` (code evidence, user clarification, approval outcome):
- `Impact`:
- `Status`: (`active` | `superseded` | `deprecated`)
- `Related Files`:
- `Follow-Up Required`:

## Operational Usage Rules
- Check active decisions before proposing new plan or generation path.
- Prefer consistency with active decisions unless new evidence requires revision.
- Mark superseded decisions explicitly instead of deleting history.

## Noise Control Rules
- Do not store low-value temporary chatter.
- Do not store speculative conclusions without evidence.
- Store only decisions with repeatable impact on future automation work.
