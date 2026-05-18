# Raw Memories

Merged stage-1 raw memories (stable ascending thread-id order):

## Thread `019df196-8715-7ab2-84c7-33cd1d9b96de`
updated_at: 2026-05-04T06:15:48+00:00
cwd: \\?\C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at
rollout_path: C:\Users\user\.codex\archived_sessions\rollout-2026-05-04T14-04-27-019df196-8715-7ab2-84c7-33cd1d9b96de.jsonl
rollout_summary_file: 2026-05-04T06-04-27-CfIq-codex_gemini_full_access_routing.md

---
description: Built a Codex-side bridge and dynamic router for `.gemini`, including folder relationship mapping, manifest-based change detection, and a user-level watcher that refreshes Codex routing when safe `.gemini` files change.
task: build full access routing from .gemini into .codex with auto-refresh
task_group: Windows Codex environment / cross-agent knowledge routing
task_outcome: success
cwd: C:\Users\user\Documents\Codex\2026-05-04\ai-add-a-codex-shortcut-at
keywords: .gemini, .codex, routing, knowledge, skills, memory, watcher, manifest, PowerShell, FileSystemWatcher, Startup shortcut, AGENTS.md, ROUTER.idx, ATLAS.idx, GROUND_KERNEL.md, EXECUTION_KERNEL.md, skill_path_router, SESSION_SHADOW.json
---

### Task 1: Build Codex bridge for .gemini

task: create C:\Users\user\.codex\GEMINI_FULL_ACCESS_ROUTING.md and update C:\Users\user\.codex\AGENTS.md to route Codex through .gemini knowledge/skills/memory

task_group: cross-agent knowledge bridge

task_outcome: success

Preference signals:
- when the user asked for “a full access routing” that lets AI use `.gemini knowledge or skills and others folder exist`, they were asking for a durable Codex-side navigation layer, not just a one-time answer.
- when the user asked to know “what they are used for and how they connected each other their relationship,” future runs should proactively map folder purpose + relationships, not just list paths.

Reusable knowledge:
- `.gemini\route.yaml` points to `./antigravity/route.yaml`, but that target was missing during bridge creation; fall back to `GEMINI.md`, `ROUTER.idx`, `ATLAS.idx`, `GROUND_KERNEL.md`, and `EXECUTION_KERNEL.md`.
- `antigravity\knowledge` is the curated knowledge library; `antigravity\memory` is historical memory/context; `antigravity\skills` are reference workflows, not native Codex skills unless converted to `C:\Users\user\.codex\skills\<name>\SKILL.md`.
- `ROUTER.idx` and `ATLAS.idx` are the best first-pass discovery anchors.

Failures and how to do differently:
- Do not try to treat `.gemini` as a single flat knowledge source; use the routing/index files first.
- Do not promote Gemini/Claude skill files to native Codex skills without conversion.

References:
- `C:\Users\user\.codex\GEMINI_FULL_ACCESS_ROUTING.md`
- `C:\Users\user\.codex\AGENTS.md`
- `C:\Users\user\.gemini\route.yaml`
- `C:\Users\user\.gemini\GEMINI.md`
- `C:\Users\user\.gemini\antigravity\knowledge\ROUTER.idx`
- `C:\Users\user\.gemini\antigravity\knowledge\ATLAS.idx`
- `C:\Users\user\.gemini\antigravity\knowledge\0_apex\GROUND_KERNEL.md`
- `C:\Users\user\.gemini\antigravity\knowledge\0_apex\EXECUTION_KERNEL.md`
- `C:\Users\user\.gemini\antigravity\knowledge\2_governance\artifacts\skill_path_router.md`

### Task 2: Build dynamic router + auto-refresh

task: create manifest-based Gemini scanner, generate C:\Users\user\.codex\GEMINI_DYNAMIC_ROUTING.md, and add a live watcher that refreshes on safe .gemini changes

task_group: change-aware routing automation

task_outcome: success

Preference signals:
- when the user asked for auto rerouting “when any changes had happen in .gemini folder or files changes,” future runs should default to change-aware regeneration rather than static docs.
- when the user asked the AI to “redo routing for those changed files in .codex,” a generated Codex-owned route + manifest is the right shape.

Reusable knowledge:
- PowerShell `Get-ChildItem` worked; `rg --files` hit `Access is denied` in this environment.
- Creating a scheduled task via `schtasks` failed with `Access is denied`; a user-level Startup shortcut plus hidden PowerShell watcher worked.
- The update script should exclude browser profiles, `.git`, caches, generated runtime noise, and credential-like files, but not exclude `SESSION_SHADOW.json` just because it contains the word `session`.
- The first script version had PowerShell quoting issues in generated Markdown; safer interpolation fixed it.

Failures and how to do differently:
- If Windows blocks task scheduler, switch to a user-level Startup shortcut and a hidden watcher script.
- If a filename filter is too broad, verify it against known memory files like `SESSION_SHADOW.json` before finalizing exclusions.

References:
- `C:\Users\user\.codex\gemini-router\Update-GeminiRouting.ps1`
- `C:\Users\user\.codex\gemini-router\Watch-GeminiRouting.ps1`
- `C:\Users\user\.codex\GEMINI_DYNAMIC_ROUTING.md`
- `C:\Users\user\.codex\gemini-router\gemini-manifest.json`
- `C:\Users\user\.codex\gemini-router\last-changes.json`
- `C:\Users\user\.codex\gemini-router\watcher.log`
- `C:\Users\user\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\Codex Gemini Router Watcher.lnk`
- final verified count: `603` safe indexed files

## Thread `019e153b-d3aa-73c3-8c94-575c0ce75cf7`
updated_at: 2026-05-11T10:51:20+00:00
cwd: \\?\C:\Users\user\Desktop\ecoworld
rollout_path: C:\Users\user\.codex\sessions\2026\05\11\rollout-2026-05-11T12-11-42-019e153b-d3aa-73c3-8c94-575c0ce75cf7.jsonl
rollout_summary_file: 2026-05-11T04-11-42-EmJp-ecoworld_free_visual_assets_and_modern_filter_ui.md

---
description: Added a reusable free-visual-asset fallback across Gemini/Codex skills and modernized the EcoWorld homepage filter panel toward the site’s clean white/green brand; latest user preference is to hide the chip scroller scrollbar while keeping horizontal scroll.
task: free visual asset sourcing + ecoworld homepage filter modernisation
task_group: c:\Users\user\Desktop\ecoworld
task_outcome: success
cwd: c:\Users\user\Desktop\ecoworld
keywords: Unsplash, Pexels, Pixabay, Material Symbols, SVG, CSS art, image generation fallback, EcoWorld, filter panel, chip scroller, scrollbar, information.txt, blueprint, design system
---

### Task 1: Free visual asset sourcing workflow

task: codex/gemini free visual asset workflow for ecoworld images
task_group: design_knowledge_and_skill_updates
task_outcome: success

Preference signals:
- when the user said they had no image-generation tool and asked to “generate images for my project ecoworld … using above technique,” they wanted a durable fallback workflow rather than a one-off answer.
- when the user asked to “write inside my codex or gemini knowledge if need for images generating” and to “update to claude code skills,” they wanted the workflow persisted in skills/knowledge, not just discussed.

Reusable knowledge:
- Added `C:\Users\user\.gemini\antigravity\skills\normal\design\FREE_VISUAL_ASSET_SOURCING.md` as the shared fallback workflow.
- Updated Gemini website/app design skills and Claude-facing image skills to reference the fallback workflow.
- Added native Codex skill `C:\Users\user\.codex\skills\free-visual-assets\SKILL.md`.
- Free asset workflow order: project-owned assets first, then Unsplash/Pexels/Pixabay, then Material Symbols/icons, SVG, CSS art, local caching, and source/license notes.

Failures and how to do differently:
- Initial edits to existing skill tails sometimes failed due to exact text mismatch; direct append with PowerShell was the reliable fallback.
- The environment did not have a working image-generation tool, so the durable solution was to formalize a non-paid fallback instead of waiting on image API access.

References:
- `C:\Users\user\.gemini\antigravity\skills\normal\design\FREE_VISUAL_ASSET_SOURCING.md`
- `C:\Users\user\.gemini\antigravity\skills\design\website\SKILL.md`
- `C:\Users\user\.gemini\antigravity\skills\design\website\02-asset-orchestration\skill.md`
- `C:\Users\user\.gemini\antigravity\skills\design\app\SKILL.md`
- `C:\Users\user\.gemini\antigravity\skills\design\app\02-asset-orchestration\skill.md`
- `C:\Users\user\.gemini\antigravity\skills\claude-frontend\07-image-spec\skill.md`
- `C:\Users\user\.gemini\antigravity\skills\claude\image-upload-spec\skill.md`
- `C:\Users\user\.gemini\antigravity\skills\claude-website\12-ui-refactor\skill.md`
- `C:\Users\user\.codex\skills\free-visual-assets\SKILL.md`
- `c:\Users\user\Desktop\ecoworld\BLUEPRINT.md`

### Task 2: EcoWorld homepage filter panel modernisation

task: modernize ecoworld homepage filter/search controls
task_group: ecoworld_frontend_design
 task_outcome: success

Preference signals:
- the user asked to “look into information.txt url see how ecoworld is look like the design theme and card, text, border... button..” -> future redesigns should anchor on the real EcoWorld brand/site reference, not generic modern styling.
- the user asked “and allow the scrolling bar to be invisible, css can change the width and color.. to 0.” -> future chip/scroll areas should keep horizontal scrolling but hide the scrollbar visually by default.

Reusable knowledge:
- `lib/components.php` now renders a richer filter panel structure with a top meta row and wrapped chip scroller.
- `css/style.css` restyles the panel with a cleaner white/green surface, softer border/shadow, search-icon treatment, better chip states, and custom select chevrons.
- The current page remains a lazy masonry layout; redesigns should preserve the no-overflow/mobile layout behavior that already passed validation.

Failures and how to do differently:
- The first style patch attempt failed because the existing CSS block had drifted; inspecting the exact live block first was necessary.
- The final requested polish is scrollbar invisibility for the chip scroller while retaining scroll functionality; use CSS scrollbar controls rather than removing overflow.

References:
- `c:\Users\user\Desktop\ecoworld\lib\components.php`
- `c:\Users\user\Desktop\ecoworld\css\style.css`
- `c:\Users\user\Desktop\ecoworld\BLUEPRINT.md`
- `c:\Users\user\Desktop\ecoworld\information.txt`
- `http://127.0.0.1:8010/index.php`

## Thread `019e1abf-b5e0-7652-bdb8-3f1678449c59`
updated_at: 2026-05-12T07:37:49+00:00
cwd: \\?\C:\Users\user\Desktop\ecoworld
rollout_path: C:\Users\user\.codex\sessions\2026\05\12\rollout-2026-05-12T13-53-52-019e1abf-b5e0-7652-bdb8-3f1678449c59.jsonl
rollout_summary_file: 2026-05-12T05-53-52-ykaJ-ecoworld_cleanup_and_php_asset_cache_busting.md

---
description: EcoWorld root cleanup removed disposable tmp/test-results artifacts; shared PHP layout now appends second-precision cache-busting versions to CSS/JS so updates load reliably.
task: remove temp/test artifact folders and add php asset versioning
task_group: C:\Users\user\Desktop\ecoworld
task_outcome: success
cwd: C:\Users\user\Desktop\ecoworld
keywords: php, cache-busting, style.css, app.js, tmp, test-results, cleanup, htmlHead.php, htmlBody.php, init.php, php -l, cdp-profile, layout-check.mjs
---

### Task 1: Cleanup disposable folders

task: delete tmp and test-results after checking safety in EcoWorld root
task_group: cleanup / filesystem hygiene
task_outcome: success

Preference signals:
- user asked to remove “all unessasary thing like testing or folder that are empty or are lagacy no use anymore” -> default to trimming clearly disposable legacy/test/empty items, but still verify runtime relevance first.
- after being told tmp and test-results were optional, user said “remove then” -> if user wants lean project root, delete temp/QA folders directly.

Reusable knowledge:
- `test-results` held QA artifacts and a large `cdp-profile` browser cache; it was not needed for runtime.
- `tmp` held local server logs and temp content; safe to delete when the user wants cleanup.
- `test-results/layout-check.mjs` was referenced in `BLUEPRINT.md`, so script references should be checked before deleting adjacent QA content.

Failures and how to do differently:
- Initial pass was conservative because some empty placeholder dirs may still be runtime placeholders; do not delete those without checking.
- The repo root was not a git repo (`git status` failed with “not a git repository”), so verification relied on `Test-Path`/directory inspection instead of git state.

References:
- Removed paths: `C:\Users\user\Desktop\ecoworld\_reference`, `C:\Users\user\Desktop\ecoworld\test-results\cdp-profile`, `C:\Users\user\Desktop\ecoworld\tmp`, `C:\Users\user\Desktop\ecoworld\test-results`
- `test-results` size before final delete was ~321,962 bytes after cache removal; before that it was ~23 MB with `cdp-profile`.
- Verification command shape: `Test-Path` returned `False` for both `tmp` and `test-results`.

### Task 2: Add asset cache busting in PHP

task: make CSS/JS reload using php datetime query strings in shared includes
task_group: PHP layout / asset loading
task_outcome: success

Preference signals:
- user asked to “set <?= datetime ?> with min sec” so custom CSS updates are forced to load -> prefer server-generated cache busting in shared includes, not per-page manual edits.
- user also asked to do it for “other css that need updating” -> when there are shared asset points, update them centrally.

Reusable knowledge:
- `lib/init.php` is the shared bootstrap for EcoWorld page templates and is a suitable place for a per-request constant.
- `lib/htmlHead.php` is the shared stylesheet include point; `lib/htmlBody.php` is the shared JS include point.
- A central constant `ECO_ASSET_VERSION = date('YmdHis')` was added and then used in query strings.
- Validated files with `php -l` and all passed.

Failures and how to do differently:
- `apply_patch` on `htmlHead.php` failed due to encoding/line mismatch; a direct PowerShell `-replace` write succeeded. For this repo, use exact string replacement if patch context is brittle.

References:
- Added in `lib/init.php`: `define('ECO_ASSET_VERSION', date('YmdHis'));`
- Updated in `lib/htmlHead.php`: `/css/style.css?v=<?= h(ECO_ASSET_VERSION) ?>`
- Updated in `lib/htmlBody.php`: `/js/app.js?v=<?= h(ECO_ASSET_VERSION) ?>`
- Validation: `php -l` reported `No syntax errors detected` for `init.php`, `htmlHead.php`, and `htmlBody.php`.

## Thread `019e1b1f-13ff-7b63-958c-8335a88c5fdd`
updated_at: 2026-05-12T07:39:07+00:00
cwd: \\?\C:\Users\user\Desktop\ecoworld
rollout_path: C:\Users\user\.codex\sessions\2026\05\12\rollout-2026-05-12T15-38-02-019e1b1f-13ff-7b63-958c-8335a88c5fdd.jsonl
rollout_summary_file: 2026-05-12T07-38-02-n2DH-read_gemini_knowledge_ecoworld_routing_hydration.md

---
description: User asked Codex to read `.gemini` knowledge; agent hydrated the Codex-to-Gemini bridge, refreshed Gemini routing, loaded core indexes/kernels, and read the active EcoWorld UI notes. Outcome was success. Highest-value takeaway: follow the bridge/index path (`00_CODEX_START_HERE.md` -> `GEMINI_FULL_ACCESS_ROUTING.md` -> router refresh -> `GEMINI_DYNAMIC_ROUTING.md` -> `route.yaml` -> `ROUTER.idx`/`ATLAS.idx`) instead of broad `.gemini` tree reads.
task: read .gemini knowledge / hydrate routing
task_group: .gemini routing and website design context
task_outcome: success
cwd: C:\Users\user\Desktop\ecoworld
keywords: .gemini, routing, bridge, ROOUTER.idx, ATLAS.idx, GROUND_KERNEL, EXECUTION_KERNEL, skill_path_router, Update-GeminiRouting.ps1, EcoWorld, website design
---

### Task 1: Read `.gemini` knowledge / hydrate routing

task: ai read .gemini knowledge
task_group: .gemini routing and website design context
task_outcome: success

Preference signals:
- The user said `ai read .gemini knowledge`, which matches the local bridge trigger and implies the agent should hydrate the `.gemini` graph directly without asking clarifying questions.
- The active open file was `ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md`, which suggests the user wanted `.gemini` knowledge relevant to the current EcoWorld website/UI work.

Reusable knowledge:
- On this machine, the bridge order is: `C:\Users\user\.codex\00_CODEX_START_HERE.md` -> `C:\Users\user\.codex\GEMINI_FULL_ACCESS_ROUTING.md` -> `Update-GeminiRouting.ps1 -Quiet` -> `C:\Users\user\.codex\GEMINI_DYNAMIC_ROUTING.md` -> `C:\Users\user\.gemini\route.yaml` -> `GEMINI.md` -> `ROUTER.idx` -> `ATLAS.idx` -> `GROUND_KERNEL.md` -> `EXECUTION_KERNEL.md` -> `skill_path_router.md`.
- `GEMINI_DYNAMIC_ROUTING.md` confirmed the EcoWorld note is indexed and the router was current, so that file is a good retrieval handle for future EcoWorld design follow-ups.
- `ROUTER.idx` and `ATLAS.idx` are the intended compact discovery layer; the bridge explicitly discourages loading the whole `.gemini` tree.

Failures and how to do differently:
- No failure; router refresh succeeded and the requested knowledge hydration completed.
- Keep the read scope narrow and route-driven for similar requests, since the bridge warns against full-tree hydration.

References:
- `Update-GeminiRouting.ps1 -Quiet` succeeded (exit code 0).
- `GEMINI_DYNAMIC_ROUTING.md` listed `ADDED: antigravity\skills\design\website\ECOWORLD_IMPLEMENTED_UI_NOTES_2026-05-12.md` and reported `Safe indexed files: 964`.
- The EcoWorld note states the finalized UI decisions: shared search/filter row, hidden chip scrollbar with mint active state, minimal text-only header, homepage hero switched from video to `images/Ebonylane-Hazelton.jpg`, About/Contact hero buttons removed, Blueprint page reverted to a focused layout, and footer inline contact icons added.

## Thread `019e200c-6eb9-73f3-a7cc-770223cf05b8`
updated_at: 2026-05-13T08:54:23+00:00
cwd: \\?\C:\Users\user\.codex
rollout_path: C:\Users\user\.codex\sessions\2026\05\13\rollout-2026-05-13T14-35-46-019e200c-6eb9-73f3-a7cc-770223cf05b8.jsonl
rollout_summary_file: 2026-05-13T06-35-46-ELIk-codex_migration_optimization_and_cross_tool_ignore.md

---
description: Migrated `.gemini` knowledge/skills into `.codex`, added cross-tool ignore files, restored a core-safe skill baseline, and rewired routing toward `.codex`; key takeaway is that the user wants plan-first, concise, low-token defaults with deep escalation only when needed, but some cleanup/migration steps were partially blocked by permissions/usage limits.
task: migrate `.gemini` knowledge/skills into `.codex`, standardize ignores, restore core-safe skills, and optimize token/speed behavior
task_group: c:\Users\user\.codex
cwd: c:\Users\user\.codex
keywords: .codex, .gemini, codex-router, codex-migrated, .claudeignore, .geminiignore, .openaiignore, plan-first, low reasoning, skills/.system, AGENTS.md, CODEX_FULL_ACCESS_ROUTING.md, CODEX_DYNAMIC_ROUTING.md, config.toml, sqlite wal, sqlite shm, memory lookup, dual-lane runtime
---

### Task 1: cross-tool ignores and plan-first policy

task: create .claudeignore/.geminiignore/.openaiignore from balanced .codexignore baseline; set plan-first and low-token defaults
task_group: config/routing hygiene
task_outcome: success

Preference signals:
- user asked to create `.claudeignore`, `.geminiignore`, and `.openaiignore` with the same balanced baseline as `.codexignore` -> wants ignore rules standardized across tools, not one-off
- user asked for “plan mode always trigger on” and later for lower token cost -> wants plan-first behavior and concise defaults

Reusable knowledge:
- `config.toml` was updated to `model_reasoning_effort = "low"` while keeping `gpt-5.3-codex`
- `.claudeignore`, `.geminiignore`, and `.openaiignore` were created with secret/runtime/cache/session ignores and explicit allow-lists for routing/knowledge files
- `AGENTS.md`, `00_CODEX_START_HERE.md`, `CODEX_FULL_ACCESS_ROUTING.md`, and the bridge instructions now express plan-first, concise-by-default, and deferred Tier-0 loading for routine tasks

Failures and how to do differently:
- root writes needed elevated access in some cases
- hash equality across the three ignore files is not expected because each has a tool-specific header comment

References:
- `.claudeignore`, `.geminiignore`, `.openaiignore`
- `config.toml`
- `AGENTS.md`
- `00_CODEX_START_HERE.md`
- `CODEX_FULL_ACCESS_ROUTING.md`
- `00_CODEX_CUSTOM_INSTRUCTIONS_GEMINI_BRIDGE.md`

### Task 2: core-safe skill restore and dual-lane runtime

task: restore minimum `.system` skills and add Lean Fast Lane / Deep Capability Lane policy
task_group: skill/runtime safety
task_outcome: partial

Preference signals:
- user wanted better skills capability completeness but explicitly preferred a core-safe baseline, not full heavy restore -> restore only what is needed, keep optional deletions
- user wanted lower token cost, faster speed, and better depth -> dual-lane runtime makes depth conditional instead of always paid for

Reusable knowledge:
- Restored `skills/.system/.codex-system-skills.marker`, `skills/.system/skill-installer`, `skills/.system/skill-creator`, `skills/.system/plugin-creator`, `skills/.system/openai-docs`, and `skills/imagegen`
- Added missing-skill fallback map so optional missing skills degrade gracefully instead of hard-failing
- Added dual-lane policy, response templates by task class, and quality gates in `AGENTS.md` and bridge docs

Failures and how to do differently:
- many optional heavy skills remain removed by design
- some capability completeness still depends on later selective restoration if the user wants those workflows again

References:
- `skills/.system/.codex-system-skills.marker`
- `skills/.system/skill-installer/SKILL.md`
- `skills/.system/skill-creator/SKILL.md`
- `skills/.system/plugin-creator/SKILL.md`
- `skills/.system/openai-docs/SKILL.md`
- `skills/imagegen/SKILL.md`
- `AGENTS.md`

### Task 3: migrate `.gemini` knowledge/resources into `.codex`

task: copy `.gemini` knowledge/skills into `.codex`, rename `libraries/gemini-migrated` to `libraries/codex-migrated`, and reroute live references
task_group: migration/routing
task_outcome: partial

Preference signals:
- user wanted `.gemini` knowledge and skills moved into `.codex` and to stop routing through `.gemini` where possible -> migrate and update links, don’t just mirror
- user wanted `knowledge` conceptually renamed to `memories` in Codex -> bridge files should use `.codex` terminology

Reusable knowledge:
- migration of the major knowledge and skill content succeeded with count/hash verification before source removal
- `libraries/gemini-migrated` was not just legacy at the time; it was still wired into live routing and therefore needed a rename rather than immediate deletion
- the new active path is `libraries/codex-migrated`
- live docs/routing were updated to prefer `.codex` paths and to remove many hardcoded `.gemini` references

Failures and how to do differently:
- `CODEX_DYNAMIC_ROUTING.md` still carried historical `REMOVED:` entries with old `gemini-migrated` strings after the router refresh, and the final rewrite was blocked by permission/usage limits
- some historical memory archives still contain `.gemini` references by design; those are not live-routing problems

References:
- `libraries/codex-migrated`
- `CODEX_DYNAMIC_ROUTING.md`
- `CODEX_FULL_ACCESS_ROUTING.md`
- `00_CODEX_START_HERE.md`
- `rules/default.rules`
- `skills/design/app/SKILL.md`
- `skills/design/website/SKILL.md`
- `skills/claude/image-upload-spec/skill.md`
- `skills/claude-frontend/07-image-spec/skill.md`
- `skills/claude-website/12-ui-refactor/skill.md`

### Task 4: legacy cleanup and root-file triage
task: audit root `.codex` files and remove low-risk legacy artifacts
task_group: cleanup
task_outcome: partial

Preference signals:
- user wanted old/useless files removed directly when low risk -> remove only when impact is clearly small
- user asked to check every root file and think through what happens if it is removed -> root-level impact analysis before deletion

Reusable knowledge:
- `.codex-global-state.json` is live state; `.codex-global-state.json.bak` was safe to remove
- `logs_2.sqlite` and `state_5.sqlite` were active runtime DBs during the check, and their WAL/SHM files were also active, so deleting them while Codex is running is unsafe
- `README.md`, `00_CODEX_PERF_BENCHMARK.md`, and similar docs are low runtime risk

Failures and how to do differently:
- WAL/SHM cleanup was correctly blocked because Codex processes were active; the safe rule is to close Codex first before touching those files
- some cleanup steps were blocked by permission/usage limits

References:
- `.codex-global-state.json`
- `.codex-global-state.json.bak`
- `logs_2.sqlite`, `logs_2.sqlite-wal`, `logs_2.sqlite-shm`
- `state_5.sqlite`, `state_5.sqlite-wal`, `state_5.sqlite-shm`

### Task 5: token/speed/depth optimization benchmarking

task: add benchmark scaffolding for low-token / faster / deeper / more complete skill validation
task_group: performance
 task_outcome: partial

Preference signals:
- user repeatedly asked for lower token cost, faster response speed, better output depth, and more complete skill coverage -> optimize for a dual-lane system, not just raw brevity
- user wanted a before/after comparison -> future optimization should be measurable, not assumed

Reusable knowledge:
- `00_CODEX_PERF_BENCHMARK.md` exists as a 10-task benchmark scaffold with token/time/turn/quality metrics
- runtime docs now tell the assistant to use targeted reads, avoid repeated reads of unchanged files, and only escalate depth when triggers apply
- prompt/memory usage is now relevance-gated rather than always-on in the bridge docs

Failures and how to do differently:
- no live token benchmark numbers were gathered in this rollout; the benchmark file is for future measurement
- some claimed speed/token improvements are policy-level estimates, not measured results

References:
- `00_CODEX_PERF_BENCHMARK.md`
- `AGENTS.md`
- `CODEX_FULL_ACCESS_ROUTING.md`
- `00_CODEX_START_HERE.md`

