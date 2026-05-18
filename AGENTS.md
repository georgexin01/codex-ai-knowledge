# Codex Global Bridge

## Codex Knowledge Bridge

Use this route at the start of each new coding/planning/design/research/recovery task.

## Auto Bootstrap (Startup-Once)

- On new chat startup in this workspace, automatically run the ultra-lean `.codex knowledge` read path once.
- Default behavior for `ai read .codex knowledge`: route-first selective-load, then lazy-load only task-relevant memory rules.
- Stop as soon as a valid route is found; do not continue scanning.
- Load `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md` and apply it as the default reasoning behavior contract.

## GitNexus — Detect-and-Use (only if installed)

GitNexus is **never auto-installed and never auto-analyzed**. The user installs and runs `gitnexus analyze` manually when they want. The agent only *uses* the graph if it already exists.

At the start of work in a code project, check for `.gitnexus/` in the project root.

- **If `.gitnexus/` exists** → prefer GitNexus MCP tools over blind grep for structural questions:
  - `impact` — blast-radius / upstream dependents before editing a function or module.
  - `context` — 360° symbol view with categorized references and process participation.
  - `query` — concept-grouped hybrid search (BM25 + semantic + RRF) instead of plain grep.
  - `detect_changes` — git-diff impact (affected processes, risk level) before commits.
  - `rename` — safe coordinated multi-file symbol rename.
- **If `.gitnexus/` is missing** → do not suggest installing it, do not run `gitnexus analyze`. Use normal grep/glob/read tools. The user decides when (and whether) to install.
- **If `gitnexus status` reports stale** → mention it once if relevant to the task; do not auto-reindex.
- **Never** run `gitnexus analyze` on `.codex` itself (knowledge, not code).

Tool reference and per-task workflow: `memories/2_governance/GITNEXUS.md`.

## Default Interaction Policy (Plan-First)

- Default to plan-first behavior for new tasks: clarify scope, define success criteria, then execute.
- Keep plans concise for routine tasks and detailed for high-risk or multi-step work.
- Switch to immediate execution when user explicitly asks to implement and scope is clear.
- Use concise responses by default; expand details only on request or when risk requires it.

## Dual-Lane Runtime Policy

- Lean Fast Lane (default): routine/self-contained tasks, small edits, simple Git/workflow support.
- Deep Capability Lane (auto-escalate): multi-file refactor, architecture/governance, security-sensitive work, unknown-root-cause debugging, or explicit asks like "deep", "thorough", or "review".
- In Deep Capability Lane, increase structure and reasoning depth while keeping scope targeted.

## Response Templates By Task Class

- Routine: short outcome + one validation line.
- Medium: concise sections with risk/checks.
- Deep: findings-first with test and rollback notes.

## Comparison Table Format (MANDATORY — user preference)

When the user asks for a "comparison table" (or any before/after comparison), every such table **MUST** include these dimensions, not just the topic columns:

| Metric | Before | After | Δ / Notes |
|---|---|---|---|
| **Token cost** | estimate (e.g. ~12k) | estimate (e.g. ~6k) | % drop |
| **Speed** | qualitative (slow / fast) | qualitative | direction |
| **Speed increase %** | — | numeric estimate (e.g. +50%) | required |
| **Rating** | x/10 | y/10 | delta |

Rules:
- Apply this format whenever the user types "comparison table" / "comparison tables", or asks for a before/after / before-vs-after layout — even if they do not explicitly list these metrics.
- If exact numbers are not measurable, give an honest estimate (e.g. "~12k → ~6k", "+~50%") and flag the estimate; never silently omit a required column.
- This is in addition to whatever topic-specific columns the comparison needs (e.g. file sizes, ratings per layer). Token / speed / speed-increase % / rating are **always present**.
- Source: user explicit standing instruction, 2026-05-15. Detail: `memories/USER_DNA.md` §5.

## Quality Gates Before Final Answer

- Correctness check: verify result matches request and actual file/tool state.
- Edge-case check: call out likely failure/compatibility edge if relevant.
- Missing-assumption check: state any assumption that can affect behavior.

## Karpathy Compliance Hook

- Mandatory: every final response must include a full 4-check Karpathy compliance block.
- Required checks (exactly four):
  - `Assumptions surfaced`
  - `Simplicity preserved`
  - `Surgical scope respected`
  - `Verification evidence included`
- Output contract:
  - each check must be marked `pass | fail | n/a`
  - each check must include one short evidence line
- Failure behavior:
  - if any check is `fail`, self-correct before finalizing
  - if self-correction is not possible, explicitly declare unresolved blocker

## Reasoning Evolution Layer

- Apply `Reasoning Evolution Protocol v1` from `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`.
- Routine tasks: compact application (goal contract, assumptions, token discipline, verification-weighted output).
- Deep/high-risk tasks: full application of all protocol rules.
- Evidence order is mandatory: file state > tests > logs > memory > inference.

## Tier-0 Rules (Deferred For Routine Tasks)

1. `C:\Users\User\.codex\memories\0_apex\GROUND_KERNEL.md` (consolidated Tier-0 kernel: APEX principles + execution loop + operational standard + edit-safety tiers)
2. `C:\Users\User\.codex\memories\0_apex\KARPATHY_TIER0_PRINCIPLES.md` (constitutional Karpathy principles: think-before-coding, simplicity-first, surgical-changes, goal-driven-execution)
3. `C:\Users\User\.codex\memories\2_governance\PREFLIGHT_CHECKLIST.md`

Load Tier-0 files for architecture/governance/recovery/high-risk work. Defer for routine tasks to reduce token usage.

## Startup Route

0. `C:\Users\User\.codex\00_CODEX_START_HERE.md`
1. `C:\Users\User\.codex\00_CODEX_CUSTOM_INSTRUCTIONS_CODEX_BRIDGE.md`
2. `C:\Users\User\.codex\00_REASONING_EVOLUTION_PROTOCOL.md`
3. `C:\Users\User\.codex\CODEX_FULL_ACCESS_ROUTING.md`
4. `C:\Users\User\.codex\CODEX_DYNAMIC_ROUTING.md`
5. Resolve knowledge root via manifest/index, not hardcoded-only path.
6. If `CODEX_DYNAMIC_ROUTING.md` / `codex-router\codex-manifest.json` is missing or stale, regenerate via `Update-CodexRouting.ps1 -Quiet`, then re-read it.
7. Optional maintenance only: `C:\Users\User\.codex\codex-router\Update-CodexRouting.ps1 -Quiet`

## Mapping Rules

- `knowledge` means `C:\Users\User\.codex\memories` (with manifest/fallback resolution)
- `skills` means `C:\Users\User\.codex\skills`
- `ai read .codex knowledge` loads `.codex` knowledge route
- Automatic NotebookLM routing: if a user prompt contains `notebooklm.google.com/notebook/` (or a clear NotebookLM notebook ID), auto-route to `C:\Users\User\.codex\memories\2_governance\bridges\notebooklm_path_bridge.md` with no extra trigger phrase required
- `ai read .codex skills` loads `.codex` skills route
- `ai claude` triggers `.codex` claude mode:
  - `skills\claude`
  - `skills\claude-frontend`
  - `skills\claude-website`
  - `skills\claude-meta`

## Boundaries

- Only load necessary files; do not hydrate full trees.
- Prefer current project files over old memory if conflict exists.
- Do not expose secrets/auth/token/cookie files unless explicitly requested and safe.
- Run memory lookup only when the task clearly depends on prior workspace history/decisions.
- Hybrid format guidance:
  - `.md` narrative/directives
  - `.yaml` high-density rules/config
  - `.json` state/index metadata
  - Read top sections/keys first and stop early when route/intent is resolved.

## Missing-Skill Fallback Map

- If optional skill folders are missing, degrade gracefully using native shell + targeted file analysis instead of failing.
- Core-safe priority skills: `.system` marker, installer/creator/routing essentials, and one fallback generation path (`skills/imagegen`).
- Treat heavy optional skills as on-demand; only require them when user explicitly asks for that workflow.

## Operational Hygiene

- Keep ignore strategy aligned across `.codexignore`, `.claudeignore`, legacy-tool ignore files, and `.openaiignore`.
- For performance hygiene, periodically clean/archive noisy local state (`logs_2.sqlite*`, session/cache artifacts) outside active tasks.

## Usage-Time Optimization Principles

- Keep prompts short and scoped to one task and explicit target files.
- Prefer `patch only` or `minimal diff` execution style unless broader refactor is requested.
- Avoid deep-review mode unless requested or risk requires it.
- Keep route-first loading for `.codex knowledge`; stop after first valid route match.
- Periodically clean runtime artifacts for performance and noise control (`.tmp`, sessions, cache, large sqlite logs) when safe to do so.
