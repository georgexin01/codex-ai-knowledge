# Codex Start Here

This is the fastest startup router for Codex on this machine.

## Priority

1. Codex system, developer, tool, safety, sandbox, and current user instructions.
2. Current project instructions: `AGENTS.md`, `BLUEPRINT.md`, and local task files.
3. Codex root bridge files in `C:\Users\User\.codex`.
4. Codex knowledge/memories/skills reference files.

## Ultra-Lean Knowledge Boot Sequence

Default profile: `Ultra-Lean`.

1. Read startup contracts only:
   - `C:\Users\User\.codex\00_CODEX_START_HERE.md`
   - `C:\Users\User\.codex\00_CODEX_CUSTOM_INSTRUCTIONS_CODEX_BRIDGE.md`
   - `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`
   - `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
2. Read `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md` to get the current index map.
3. Resolve knowledge root from manifest/index data, not hardcoded path assumptions.
4. If `CODEX_DYNAMIC_ROUTING.md` / `codex-router\codex-manifest.json` is missing or stale, regenerate via `Update-CodexRouting.ps1 -Quiet`, then re-read it.
5. Stop after first valid route match. Do not continue scanning.

## Tier-0 Deferred Deep Read

Load Tier-0 files only when the task is architecture/governance/recovery-sensitive, high-risk, or explicitly requests deep policy context:

1. `C:\Users\User\.codex\memories\0_apex\GROUND_KERNEL.md` (consolidated Tier-0 kernel: APEX principles + execution loop + operational standard + edit-safety tiers)
2. `C:\Users\User\.codex\memories\0_apex\KARPATHY_TIER0_PRINCIPLES.md` (constitutional behavior rules for coding and review quality)
3. `C:\Users\User\.codex\memories\2_governance\PREFLIGHT_CHECKLIST.md`

These are absolute principles/rules for behavior and execution style and are deferred for routine tasks to reduce token usage.

## Fast Read Order

1. `C:\Users\User\.codex\00_CODEX_CUSTOM_INSTRUCTIONS_CODEX_BRIDGE.md`
2. `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
3. Run `C:\Users\User\.codex\codex-router\Update-CodexRouting.ps1 -Quiet` when shell/approvals allow.
4. `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md`
5. `C:\Users\User\.codex\codex-router\codex-manifest.json` (full file index: descriptions + paths)
6. If route is unclear, fall back to:
   - `C:\Users\User\.codex\memories\2_governance\artifacts\skill_path_router.md`

## Token-Saving Runtime Policy

- Default response style is concise. Expand only when the user asks for more detail or risk requires it.
- Start with targeted reads (`rg`, specific files) and avoid broad tree scans unless blocked.
- Batch parallel file reads once and avoid repeated re-reads unless files changed.
- Keep default reasoning low; escalate reasoning only for complex/high-risk tasks or explicit user request.
- Run memory lookup only when the task clearly depends on prior decisions/workspace history.

## Reasoning Evolution Layer

- Load and apply `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md` at startup.
- For routine tasks, apply compact reasoning rules with low overhead.
- For deep/high-risk tasks, apply full protocol including counterexample check and rollback-aware output.

## Hybrid Format Read Rules

- Treat `.md` as narrative and directives.
- Treat `.yaml` as high-density rules/config references.
- Treat `.json` as state/index metadata.
- Read top sections/keys first and stop early when route/intent is resolved.
- Avoid full-file hydration unless required for the active task.

## First-Pass Guardrails

- Do not recurse full trees under `memories`, `skills`, or `libraries` in first pass.
- Do not read historical rollouts/artifacts unless explicitly needed.
- Keep Tier-0 deferred unless deep, high-risk, governance, or recovery context is required.
- Normalize paths to `C:\Users\User\.codex` in runtime checks and use fallback resolution when manifest paths are stale.

## Auto-Escalation Triggers

- Escalate to Deep Capability Lane for: multi-file refactors, architecture/governance, security-sensitive changes, unknown-root-cause debugging, or explicit "deep/thorough/review" asks.
- Stay in Lean Fast Lane for routine/self-contained tasks.

## Trigger Phrases

- `ai read .codex knowledge` -> route-first selective-load: minimal route context first, then lazy-load only task-relevant memory rules
- Automatic route: any prompt containing `notebooklm.google.com/notebook/` auto-loads `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md` (no `ai notebooklm` command required)
- `ai notebooklm <url|id>` -> use `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md` for path intake, NotebookLM research workflow, and fallback handoff when direct notebook access is unavailable
- `ai read .codex skills` -> load from `C:\Users\User\.codex\skills`
- `ai claude` -> route first to:
  - `C:\Users\User\.codex\skills\claude`
  - `C:\Users\User\.codex\skills\claude-frontend`
  - `C:\Users\User\.codex\skills\claude-website`
  - `C:\Users\User\.codex\skills\claude-meta`
- `ai design app` -> `C:\Users\User\.codex\skills\design\app`
- `ai design website` -> `C:\Users\User\.codex\skills\design\website`

## Loading Rule

Do not read full trees. Load router/index files, then only task-relevant files.
