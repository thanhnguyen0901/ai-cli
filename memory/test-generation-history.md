# Test Generation History Memory

## Purpose
- Record AI-assisted generation outcomes to preserve rationale, avoid duplicate work, and improve later planning quality.

## History Entry Schema
- `Entry ID`:
- `Date/Session`:
- `Test Objective`:
- `Framework Used`:
- `Reused Assets`:
- `New Files Created`:
- `Modified Files`:
- `Major Decisions`:
- `Follow-Up Notes`:
- `Outcome Status`: (`generated` | `deferred` | `blocked`)

## Usage Rules
- Check recent entries before starting similar generation requests.
- Reuse successful approaches where constraints are comparable.
- Avoid repeating previously rejected approaches unless requirements changed.

## Quality Rules
- Keep entries concise, factual, and file-referenced.
- Record only meaningful generation events, not every discussion message.
- Link blockers to gap/risk records when applicable.

## Refresh and Maintenance Rules
- Append new entry after each approved generation cycle.
- Update existing entry when follow-up fixes materially change outcome.
- Archive or summarize very old entries when noise reduces usefulness.
