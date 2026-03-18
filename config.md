# Config

## Configuration

### Runtime Profile
- `system_name`: `ai-cli`
- `operating_mode`: `controlled_cli`
- `interaction_model`: `prompt_driven`

### Framework Mode
- `framework_mode`: `hybrid`
- Allowed values: `cypress`, `playwright`, `hybrid`
- Behavior:
  - `cypress`: use Cypress workflows/patterns only
  - `playwright`: use Playwright workflows/patterns only
  - `hybrid`: detect per task and enforce framework isolation per output

### Language Defaults
- `default_language`: `typescript`
- Allowed values: `javascript`, `typescript`

### Safety and Approval
- `strict_mode`: `true`
- `approval_required`: `true`
- `reuse_first`: `true`
- `source_of_truth`: `codebase`
- `allow_assumption_without_evidence`: `false`

### Context and Memory
- `auto_context_update`: `on_approved_generate`
- Allowed values: `off`, `manual_only`, `on_approved_generate`
- `memory_refresh_policy`: `prompt_on_start`
- Allowed values: `always`, `prompt_on_start`, `manual_only`
- `memory_staleness_default`: `assume_stale_until_validated`

### Startup Behavior
- `startup_trigger`: `START`
- `startup_load_order`: `config -> rules -> workflows -> frameworks -> context -> memory`
- `startup_requires_readiness_report`: `true`
- `startup_requires_learning_prompt`: `true`

### Learning Behavior
- `learning_requires_explicit_confirmation`: `true`
- `learning_scope_default`:
  - repository structure
  - automation architecture
  - helpers and custom commands
  - page objects and selectors
  - naming and test patterns
- `learning_result_required`: `context_and_memory_status_update`

### Response Style
- `response_style`: `structured_cli`
- `tone`: `direct`
- `verbosity`: `concise_with_required_detail`
- `free_form_chat`: `disabled`

## Configuration Semantics
- This file is authoritative for runtime behavior of AI-CLI startup and operation.
- If config conflicts with non-code narrative notes, this config wins.
- `approval_required: true` is a hard gate: no code generation before explicit approval.
- `source_of_truth: codebase` means context/memory can guide but cannot override observed code.
- `reuse_first: true` requires scanning for reusable components before proposing new abstractions.
- `framework_mode: hybrid` does not permit API mixing inside a single implementation unless the repository explicitly requires it.
- `memory_refresh_policy: prompt_on_start` requires asking the user at startup whether to learn/refresh.
- `auto_context_update: on_approved_generate` means context/memory updates run after approved generation workflows; manual update remains available from menu.

## Application Rules
- The assistant must read and apply this config on every `START` sequence.
- If a key is invalid or missing, fallback behavior is:
  - keep strict mode and approval required enabled,
  - report config warning in startup status,
  - continue in safe mode.
- The assistant must surface active config values in startup response under `Configuration Applied`.
