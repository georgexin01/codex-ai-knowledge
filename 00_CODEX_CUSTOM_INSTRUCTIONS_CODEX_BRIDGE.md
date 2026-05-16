# Codex Custom Instructions: Codex Knowledge Bridge

This workspace uses `.codex` as the primary knowledge, memories, and skills source.

## Ultra-Lean Knowledge Boot Sequence

Default profile: `Ultra-Lean`.

1. Read startup contracts first:
   - `C:\Users\User\.codex\00_CODEX_START_HERE.md`
   - `C:\Users\User\.codex\00_CODEX_CUSTOM_INSTRUCTIONS_CODEX_BRIDGE.md`
   - `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`
   - `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
2. Read `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md` for current index map.
3. Resolve knowledge root from manifest/index data, not hardcoded path assumptions.
4. If `CODEX_DYNAMIC_ROUTING.md` / `codex-router\codex-manifest.json` is missing or stale, regenerate via `Update-CodexRouting.ps1 -Quiet`, then re-read it.
5. Stop after first valid route match and do not continue scanning.

## Tier-0 Absolute Rules

Read these for architecture/governance/recovery/high-risk tasks or when explicitly requested:

1. `C:\Users\User\.codex\memories\0_apex\GROUND_KERNEL.md` (consolidated Tier-0 kernel: APEX principles + execution loop + operational standard + edit-safety tiers)
2. `C:\Users\User\.codex\memories\2_governance\PREFLIGHT_CHECKLIST.md`

These define must-follow principles and execution behavior and are deferred for routine tasks to reduce token usage.

## Main Sources

- Knowledge/memories: `C:\Users\User\.codex\memories`
- Skills: `C:\Users\User\.codex\skills`

## Routing

1. `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
2. `C:\Users\User\.codex\codex-router\Update-CodexRouting.ps1 -Quiet`
3. `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md`
4. `C:\Users\User\.codex\codex-router\codex-manifest.json`
5. `C:\Users\User\.codex\memories\2_governance\artifacts\skill_path_router.md`

## Runtime Defaults

- Plan-first by default for new tasks; execute directly when scope is clear and user requests implementation.
- Use concise responses by default.
- Keep default reasoning low; escalate for complex/high-risk/explicitly requested deep reasoning.
- Run memory lookup only when the task clearly depends on prior decisions or workspace history.
- Prefer targeted reads and avoid broad scans unless needed.
- Deep Capability Lane triggers: multi-file refactor, architecture/governance, security, unknown-root-cause debugging, or explicit "deep/thorough/review".
- Before final output, run three quality gates: correctness, edge-case, and missing-assumption checks.
- Apply `Reasoning Evolution Protocol v1` from `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`.

## Hybrid Format Read Rules

- Treat `.md` as narrative and directives.
- Treat `.yaml` as high-density rules/config references.
- Treat `.json` as state/index metadata.
- Read top sections/keys first and stop early once route/intent is resolved.
- Avoid full-file hydration unless the active task requires it.

## First-Pass Guardrails

- Do not recurse full trees under `memories`, `skills`, or `libraries` in first pass.
- Do not load historical rollouts/artifacts unless explicitly needed.
- Keep Tier-0 deferred unless deep/high-risk/governance/recovery context is required.
- Normalize to `C:\Users\User\.codex` and use fallback resolution when manifest paths are stale.

## Trigger Mapping

- `ai read .codex knowledge` -> route-first selective-load: minimal route context first, then lazy-load only task-relevant memory rules
- Automatic route: any prompt containing `notebooklm.google.com/notebook/` auto-routes to `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md`
- `ai notebooklm <url|id>` -> use `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md` for path intake and token-lean research handoff
- `ai read .codex skills` -> `C:\Users\User\.codex\skills`
- `ai claude` -> `skills\claude`, `skills\claude-frontend`, `skills\claude-website`, `skills\claude-meta`
- `ai design app` -> `skills\design\app`
- `ai design website` -> `skills\design\website`

## Safety

- Do not read or expose secrets/auth/token/cookie/session files unless explicitly requested and safe.
- Load only relevant files for the task; do not bulk-hydrate entire trees.
- If optional skill folders are missing, continue with native fallback workflows instead of failing.

## Format & Index Discipline (Primary Rule)

Goal: cut token waste, raise speed, and avoid reading whole files.

- **Index-first read**: resolve intent from router/manifest entries (`description` + `triggers`) before opening any file. Open a file only when the task actually needs its body. Never hydrate full trees.
- **Mandatory frontmatter**: every knowledge/skill file MUST carry a tight `description:` (one specific line) and `triggers:`. The index exposes these so the agent routes without reading the file.
- **Format-match the content** when creating or rewriting knowledge:
  - `.md` â€” narrative, directives, skills (humans edit these). Token-heaviest; use only where prose is needed.
  - `.yaml` â€” rules, principles, config, checklists, frontmatter. ~30% denser than equivalent MD prose; still readable.
  - `.json` â€” state, manifests, indexes. Machine state â€” queried, not read.
  - `.toon` â€” large repetitive/tabular data (file lists, route tables). Most compact.
- **Stop early**: read top sections/keys first; stop as soon as route/intent is resolved.
- Reference: `memories/0_apex/HYBRID_FORMAT_PROTOCOL.md`.
