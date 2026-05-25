v1

## User Profile
The user works with Codex as a local Windows coding partner and wants durable reuse, not chat-only fixes. They often ask for bridges, docs, or memory that let future agents understand folder relationships and resume without re-research. Their design feedback is direct and iterative; when a request sounds like "tag design" or another broad visual tweak, they usually mean presentation polish first, not behavior changes. Current design taste signals emphasize 700-weight typography, 6px linear elements, glass overlays, strong contrast, and clickable/high-area interactions. They care about efficient routing: use compact indexes and relationship maps first, then deepen only where needed.

## User preferences
- When the user asks for "a full access routing" or says AI should understand how folders "connected each other their relationship", build a durable Codex-side bridge/read order instead of giving a one-off explanation.
- When the user asks for auto rerouting on file changes, prefer change-aware regeneration with Codex-owned outputs instead of static notes.
- Terse run requests like `admin-panel-angel pnpm run dev:local this` should be treated as direct execution requests, not planning prompts.
- When a design request is phrased broadly and visually, default to presentation, active-state, and cross-screen consistency work before touching logic.
- On this Windows PowerShell setup, switch to `pnpm.cmd` or `npm.cmd` when bare `pnpm` / `npm` is blocked by execution policy.
- For video fields, keep labels/platform wording generic (`Video URL`), not hardcoded to YouTube.
- In Vben panels with no real notification backend, disable the mock bell (`widget.notification: false`) by default.
- If the user asks for a comparison table, include Before, After, Token cost, Speed, Speed increase %, and Rating; estimate honestly when exact numbers are unavailable.

## General Tips
- For `.gemini` knowledge reads, route-first beats broad hydration: start from bridge/index files such as `GEMINI_FULL_ACCESS_ROUTING.md`, `ROUTER.idx`, and `ATLAS.idx`.
- `route.yaml` may not be sufficient on its own; if it points at a missing target, fall back to `GEMINI.md` plus the index/kernel files.
- If `.gemini` scanning hits `Access is denied`, PowerShell `Get-ChildItem` is the reliable fallback.
- For local frontend verification, do not trust a port alone; confirm the owning process is the target app's `node.exe` / Vite command line.
- In `C:\Users\user\Desktop\zenius`, `template/` is the editable app and `zenius-tech-2026/` is the read-only source.
- In `admin-panel-angel/apps/web-antd`, `dev:local` maps to `pnpm vite --mode development.localhost`, and the verified listener from memory is `http://localhost:6006/`.
- GitNexus is allowlisted, not default: use it for Vben admin / large Supabase admin work, and skip it for websites or small app repos.

## What's in Memory

### C:\Users\user\Desktop\zenius

#### 2026-05-22

- Zone 1/2/3 tag design update in `template/`: zenius, template, zone tag, zone-tag-rail, HomeView.vue, StandingsView.vue, style.css, npm.cmd
  - desc: Search this first for `template/` selector redesign work, especially when the same visual control appears on Home and Standings and must stay consistent; applies to `cwd=C:\Users\user\Desktop\zenius\template`.
  - learnings: Treat "tag design" as presentation-first; update both selector implementations together and verify with `npm.cmd run build` if PowerShell blocks `npm`.

### C:\Users\user\Desktop\angel-interior

#### 2026-05-20

- `admin-panel-angel` `dev:local` startup and listener verification: admin-panel-angel, apps/web-antd, pnpm.cmd, dev:local, Vite, vite.config.mts, localhost:6006
  - desc: Search this first when the user wants the Angel admin started locally or when Vite launch succeeds/fails differently under Windows sandboxing; applies to `cwd=C:\Users\user\Desktop\angel-interior\admin-panel-angel\apps\web-antd`.
  - learnings: Launch with `pnpm.cmd`, and if Vite throws `Access is denied` / `Could not resolve ... vite.config.mts`, retry unrestricted and verify the real `node.exe` listener before reporting success.

### C:\Users\user\.codex

#### 2026-05-04

- Codex bridge for `.gemini` knowledge and auto-refresh routing: .gemini, .codex, GEMINI_FULL_ACCESS_ROUTING.md, ROUTER.idx, ATLAS.idx, GEMINI_DYNAMIC_ROUTING.md, Update-GeminiRouting.ps1, SESSION_SHADOW.json
  - desc: Search this first for cross-agent knowledge reuse, `.gemini` hydration, or change-aware routing work in Codex home; dominant scope is `cwd=C:\Users\user\.codex` even though the rollout started from a separate working folder.
  - learnings: Build bridges around indexes and relationship maps, not broad tree reads; `Get-ChildItem` plus manifest hashing was the reliable Windows path, and `SESSION_SHADOW.json` should stay routable.

### Older Memory Topics

No additional older topics are currently represented outside the recent active window.
