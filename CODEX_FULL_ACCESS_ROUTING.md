# Codex Full Access Routing

Codex-native routing for this repository.

## Root Locations

- Knowledge/memories: `C:\Users\User\.codex\memories`
- Skills: `C:\Users\User\.codex\skills`

## Ultra-Lean Knowledge Boot Sequence

Default profile: `Ultra-Lean`.

1. Read startup docs only:
   - `C:\Users\User\.codex\00_CODEX_START_HERE.md`
   - `C:\Users\User\.codex\00_CODEX_CUSTOM_INSTRUCTIONS_CODEX_BRIDGE.md`
   - `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`
   - `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
2. Read `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md` for current map.
3. Resolve knowledge root from manifest/index, not hardcoded path.
4. If `CODEX_DYNAMIC_ROUTING.md` / `codex-router\codex-manifest.json` is missing or stale, regenerate via `Update-CodexRouting.ps1 -Quiet`, then re-read it.
5. Stop after first valid route match and do not continue scanning.

## Tier-0 Deferred Deep Read

Read Tier-0 files when the task is architecture/governance/recovery-sensitive, high-risk, or explicitly asks for deep policy grounding:

1. `C:\Users\User\.codex\memories\0_apex\GROUND_KERNEL.md` (consolidated Tier-0 kernel: APEX principles + execution loop + operational standard + edit-safety tiers)
2. `C:\Users\User\.codex\memories\2_governance\PREFLIGHT_CHECKLIST.md`

## Mandatory Startup Route (Minimal)

1. `C:\Users\User\.codex\00_CODEX_START_HERE.md`
2. `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
3. `C:\Users\User\.codex\codex-router\Update-CodexRouting.ps1 -Quiet`
4. `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md`
5. `C:\Users\User\.codex\codex-router\codex-manifest.json`
6. `C:\Users\User\.codex\memories\2_governance\artifacts\skill_path_router.md`

## Runtime Policy

- Keep default reasoning low and escalate only for complex/high-risk tasks or explicit user request.
- Prefer concise output by default; expand on user request or risk-driven need.
- Use targeted reads and avoid broad scans unless blocked.
- Avoid repeated reads of unchanged files.
- Use memory lookup by relevance, not by default for self-contained tasks.
- For deep asks ("deep/thorough/review"), use findings-first structure with test + rollback notes.
- Apply `Reasoning Evolution Protocol v1` from `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`.

## Hybrid Format Read Rules

- Treat `.md` as narrative and directives.
- Treat `.yaml` as high-density rules/config references.
- Treat `.json` as state/index metadata.
- Read top sections/keys first and stop early when route/intent is resolved.
- Avoid full-file hydration unless needed for the current task.

## First-Pass Guardrails

- No full-tree recursion under `memories`, `skills`, or `libraries`.
- No historical rollouts/artifacts in first pass unless explicitly needed.
- Tier-0 stays deferred except deep/high-risk/governance/recovery requests.
- Normalize runtime path checks to `C:\Users\User\.codex`; apply fallback when manifest points to stale profile variants.

## Trigger Map

- `ai read .codex knowledge` -> route-first selective-load: minimal route context first, then lazy-load only task-relevant memory rules
- Automatic route: any prompt containing `notebooklm.google.com/notebook/` auto-routes to `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md`
- `ai notebooklm <url|id>` -> use `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md` for notebook path intake and research handoff
- `ai read .codex skills` -> `C:\Users\User\.codex\skills`
- `ai claude` -> `.codex` claude mode:
  - `skills\claude`
  - `skills\claude-frontend`
  - `skills\claude-website`
  - `skills\claude-meta`
- `ai design app` -> `skills\design\app`
- `ai design website` -> `skills\design\website`

## Practical Loading

- Route through indexes first.
- Read only required files.
- Prefer current project files over historical memory when conflicts exist.

## Safety

- Do not expose secrets/auth/token/cookie/session files unless explicitly requested and safe.
- If optional skill paths are missing, fall back to native shell/tool workflows and continue without hard failure.
