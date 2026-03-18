# Reusable Code Map Memory

## Purpose
- Track concrete reusable automation assets currently available in the codebase.
- Reduce duplication by guiding reuse-first implementation decisions.

## Reusable Asset Schema
- `Asset Name`:
- `Category`:
- `Framework Scope`: (`cypress` | `playwright` | `shared`)
- `File Path`:
- `Primary Purpose`:
- `Typical Usage`:
- `Limitations/Constraints`:
- `Evidence Source`:
- `Confidence`: (`high` | `medium` | `low`)

## Required Asset Categories
- Login/auth helpers.
- Page objects.
- Navigation helpers.
- Table/form helpers.
- Data builders.
- Assertion helpers.
- Network helpers.
- Utility wrappers.

## Reuse Decision Rules
- Check this map before proposing new abstraction.
- Prefer adapting existing assets when behavior is close and stable.
- Propose new assets only when verified gap exists.

## Verification Rules
- Never assume an asset exists without code evidence.
- Mark unverified references clearly and avoid using them for generation.
- Remove entries that no longer resolve to active code.

## Refresh Rules
- Update map after learning, rescans, and approved generation changes.
- Add limitation notes when reuse fails due to scope or design constraints.
