# Codegen Checklist Template

## Usage
- Complete this checklist immediately before any code generation step.
- Any unchecked critical item blocks generation.

## Pre-Generation Checklist
- [ ] Approval confirmed from user (`APPROVE` state passed)
- [ ] Framework confirmed (`cypress` or `playwright`)
- [ ] Existing reusable code reviewed (helpers/page objects/commands/fixtures)
- [ ] No duplicate abstraction planned
- [ ] Target files identified (modify vs create)
- [ ] Naming conventions verified against repository patterns
- [ ] Selector strategy aligned with project standards
- [ ] Assertions mapped to expected outcomes
- [ ] Async/wait strategy explicitly defined
- [ ] Risks and ambiguities documented
- [ ] Scope limited strictly to requested task

## Optional Quality Checks
- [ ] Test data dependencies identified
- [ ] Error-path behavior considered
- [ ] Cross-file impact reviewed for regressions

## Generation Decision
- `Checklist Status`: (`pass` | `blocked`)
- `Blocking Items`:
- `Next Action`: (`generate now` | `return to discuss/explain` | `request clarification`)
