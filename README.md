# AI-CLI

AI-CLI is a prompt-driven, command-line style AI system for test automation projects. It is designed to be copied into an automation repository and used by QA engineers, automation engineers, and developers to run a controlled workflow from analysis to approved code generation.

AI-CLI is not a free-form chat assistant. It enforces structured execution, explicit approval gates, and codebase-first decision-making.

## Key Features
- CLI-style AI interaction with explicit state transitions.
- Controlled workflow: no immediate code generation.
- Codebase learning and refresh flow.
- Context + memory layers to reduce repeated scanning and improve consistency.
- Multi-framework support for Cypress and Playwright.
- Reuse-first generation strategy to avoid duplicate abstractions.

## Architecture Overview
AI-CLI is organized into layers with clear responsibilities:

- `rules/`
  - Global governance and hard constraints.
  - Defines operating behavior, approval gates, source-of-truth policy, and generation safety.
- `workflows/`
  - State-driven execution behavior (setup, learn, analyze, discuss, explain, approve, update).
- `frameworks/`
  - Cypress and Playwright adapter guides for syntax, patterns, structure, and review quality.
- `context/`
  - Stable operational knowledge models (architecture, selectors, risks, reusable patterns).
- `memory/`
  - Evolving project memory (indexes, decisions, generation history, current gaps).
- `templates/`
  - Structured output formats for analysis, solution planning, context updates, and pre-generation checklists.
- Root control files
  - `start.md`: startup contract.
  - `config.md`: runtime behavior and defaults.
  - `main-menu.md`: user action routing after setup.

How they interact:
- `start.md` + `config.md` initialize behavior.
- `rules/` enforce constraints across all workflows.
- `workflows/` drive state transitions.
- `frameworks/` provide implementation and review adapters per target framework.
- `templates/` standardize outputs for repeatability.
- `context/` and `memory/` are updated as learning and generation progress.

## How It Works (Lifecycle)
AI-CLI follows a controlled lifecycle:

`START`  
`-> SETUP`  
`-> LEARN` (optional but recommended)  
`-> READY`  
`-> ANALYZE TEST`  
`-> SOLUTION REVIEW`  
`-> DISCUSS / EXPLAIN / APPROVE`  
`-> GENERATE`  
`-> CONTEXT UPDATE`  
`-> RETURN TO MENU`

Core behavior:
- Analyze first.
- Propose solution before coding.
- Require explicit approval.
- Generate minimal scoped changes.
- Update context/memory with verified learnings.

## Quick Start Guide
1. Copy the `ai-cli/` folder into your automation repository root.
2. Open your AI assistant environment (for example ChatGPT or Copilot).
3. Paste `START`.
4. Follow the CLI-style startup prompts.
5. Choose whether to learn/refresh the current codebase.
6. Select `Generate Test From Manual Steps` from the menu and continue the guided flow.

## Example Usage
Example user inputs:
- `START`
- `yes` (learn codebase)
- `2` (generate test from manual steps)
- Paste manual test steps and expected outcomes

What AI-CLI does next:
1. Scans and summarizes relevant codebase areas.
2. Produces structured test analysis.
3. Produces a reusable-first solution plan.
4. Requests explicit approval.
5. Generates code only after approval.
6. Offers context/memory update after generation.

## Folder Structure
```text
ai-cli/
├── start.md
├── main-menu.md
├── config.md
├── workflows/
├── rules/
├── frameworks/
│   ├── cypress/
│   └── playwright/
├── context/
├── memory/
└── templates/
```

Major folders:
- `workflows/`: execution state definitions.
- `rules/`: hard behavior constraints.
- `frameworks/`: framework-specific adapters.
- `context/`: stable project knowledge models.
- `memory/`: evolving project records and decisions.
- `templates/`: reusable output structures.

## Context vs Memory
- Context (`context/`)
  - Stable, policy-oriented operational knowledge.
  - Used as a durable reference model for execution behavior.
- Memory (`memory/`)
  - Evolving, project-specific findings and history.
  - Updated after learning, discussion, and generation outcomes.

Why both exist:
- Context keeps execution consistent.
- Memory keeps project understanding current over time.

## Supported Frameworks
AI-CLI supports:
- Cypress
- Playwright

Framework selection is determined by:
- configured mode in `config.md` (`cypress`, `playwright`, `hybrid`), and
- learned repository reality during codebase analysis.

## Rules and Behavior
AI-CLI enforces the following constraints:
- No immediate code generation.
- Explicit approval required before generation.
- Reuse-first implementation decisions.
- Codebase is the source of truth.
- No hallucinated helpers, selectors, business logic, or architecture facts.
- Structured outputs over free-form chat behavior.

## When to Update Context/Memory
Update should happen:
- After codebase learning or refresh.
- After important clarification discussions that affect repeatable behavior.
- After generation introduces reusable patterns, files, or decisions.

Update quality requirements:
- Evidence-based.
- Concise and structured.
- Conflict-aware (codebase overrides stale notes).

## Limitations
- AI-CLI is prompt-driven, not a native executable CLI tool yet.
- Behavior depends on AI session continuity and model adherence.
- Requires manual user interaction for state progression.
- Accuracy depends on repository clarity and available code evidence.

## Future Improvements
- Real CLI wrapper (for example Node.js command entrypoint).
- Automated context/memory update tooling.
- CI/CD integration for validation and policy checks.
- Optional UI shell for workflow navigation.

## Contribution Guide
To extend AI-CLI safely:
- Update `rules/`, `workflows/`, and `templates/` together when behavior changes.
- Keep framework-specific guidance inside `frameworks/` adapters.
- Preserve context vs memory separation.
- Maintain strict approval gating and source-of-truth policy.
- Validate end-to-end consistency before merging changes.
