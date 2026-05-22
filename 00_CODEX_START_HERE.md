# Codex Start Here

This is the fastest startup router for Codex on this machine.

## Priority

1. Codex system, developer, tool, safety, sandbox, and current user instructions.
2. Current project instructions: `AGENTS.md`, `BLUEPRINT.md` (project-level, optional), and local task files.
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

- `ai read .codex knowledge` → route-first selective-load: minimal route context first, then lazy-load only task-relevant memory rules
- `ai read .codex skills` → `C:\Users\User\.codex\skills` (see `skill_path_router.md` for full index)
- `ai claude` → `C:\Users\User\.codex\skills\claude\WORKING_PROGRESS.md` (Vben Admin module builder — linear executor)
- `ai claude app` → `C:\Users\User\.codex\skills\claude-app\WORKING_PROGRESS.md` (mobile app Vue builder — linear executor)
- `ai claude website` → `C:\Users\User\.codex\skills\claude-website\WORKING_PROGRESS.md` (PHP + Supabase REST builder — linear executor)
- DB handshake shared by the 3 builders above → `C:\Users\User\.codex\skills\SHARED_DB_CONTRACT.md`
- `ai claude meta` → `C:\Users\User\.codex\skills\claude-meta\SKILL.md`
- `ai design app` → `C:\Users\User\.codex\skills\design\app\SKILL.md`
- `ai design website` → `C:\Users\User\.codex\skills\design\website\SKILL.md`
- `ai design spec` → `C:\Users\User\.codex\skills\design\_spec\SKILL.md` (DESIGN.md contract/lint)
- `ai karpathy` → `C:\Users\User\.codex\skills\karpathy-guidelines\SKILL.md`
- `ai imagegen` → `C:\Users\User\.codex\skills\imagegen\SKILL.md`
- `ai notebooklm <url|id>` → create `memories/2_governance/bridges/notebooklm_path_bridge.md` on first use

## Loading Rule

Do not read full trees. Load router/index files, then only task-relevant files.

## Main Sources

- Knowledge/memories: `C:\Users\User\.codex\memories`
- Skills: `C:\Users\User\.codex\skills`

## Practical Loading

- Route through indexes first.
- Read only required files.
- Prefer current project files over historical memory when conflicts exist.

## Safety

- Do not read or expose secrets/auth/token/cookie/session files unless explicitly requested and safe.
- Load only relevant files for the task; do not bulk-hydrate entire trees.
- If optional skill folders are missing, continue with native fallback workflows instead of failing.

## Format & Index Discipline (Primary Rule)

Goal: cut token waste, raise speed, and avoid reading whole files.

- **Index-first read**: resolve intent from router/manifest entries (`description` + `triggers`) before opening any file. Open a file only when the task actually needs its body. Never hydrate full trees.
- **Mandatory frontmatter**: every knowledge/skill file MUST carry a tight `description:` (one specific line) and `triggers:`. The index exposes these so the agent routes without reading the file.
- **Format-match the content** when creating or rewriting knowledge:
  - `.md` — narrative, directives, skills (humans edit these). Token-heaviest; use only where prose is needed.
  - `.yaml` — rules, principles, config, checklists, frontmatter. ~30% denser than equivalent MD prose; still readable.
  - `.json` — state, manifests, indexes. Machine state — queried, not read.
  - `.toon` — large repetitive/tabular data (file lists, route tables). Most compact.
- **Stop early**: read top sections/keys first; stop as soon as route/intent is resolved.
- Reference: `memories/0_apex/HYBRID_FORMAT_PROTOCOL.md`.
