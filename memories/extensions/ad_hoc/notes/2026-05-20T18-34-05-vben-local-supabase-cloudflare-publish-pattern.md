# Vben Admin + Local Supabase + Cloudflare Tunnel Publish Pattern

Date: 2026-05-20
Workspace source: `C:\Users\user\Desktop\angel-interior`
Intent: reusable deployment knowledge for similar Vben admin + local Supabase projects that need a public production frontend while keeping backend/auth/database on a developer PC through Cloudflare Tunnel.

## Reusable Pattern

Use this pattern when:
- frontend is a Vben admin panel
- backend/auth/storage come from local Docker Supabase
- production frontend should call a public hostname that tunnels to local Supabase
- Windows PowerShell is the operating environment

Flow:
1. Confirm active project authority and schema/project contract first.
2. Make production env point to the public tunnel hostname, not `localhost`.
3. Verify local Supabase health before touching frontend deploy.
4. Install/login/create Cloudflare tunnel and route DNS hostname to the tunnel.
5. Write `C:\Users\<user>\.cloudflared\config.yml` to proxy the public hostname to `http://127.0.0.1:54321`.
6. Install `cloudflared` as a Windows service so the tunnel survives reboots.
7. Build frontend production with Windows-safe `pnpm.cmd build:antd`.
8. Upload the newest `apps/web-antd/dist.zip` to hosting and hard-refresh browser cache.

## Key Lessons From Angel Interior

- `auth/v1/health = 200` does not prove `/rest/v1/` is healthy. Check both.
- If `supabase stop` was run, public tunnel will return `502` until `supabase start` runs again.
- `supabase status` may show some services stopped; for this pattern, verify `rest` specifically, not only auth.
- A live login error `Invalid login credentials` means the request reached Supabase Auth. At that point, likely causes are:
  - old frontend build still served by hosting
  - wrong email/password for the currently exposed local Supabase stack
- Compare hashed bundle names between local `dist` and the live site to detect stale hosting deploys.
- For Angel, local latest build had a different bootstrap hash from the live site; that was evidence the uploaded build was stale.

## Windows-Specific Rules

- Use `pnpm.cmd`, not bare `pnpm`, when PowerShell policy blocks script shims.
- `supabase status` may require elevated access on Windows because Docker pipe access can be denied in non-elevated sessions.
- `cloudflared service install` requires a PowerShell session truly running as Administrator.
- `cloudflared` may install successfully but still not be visible in the current shell PATH until a new shell starts; direct path fallback is:
  - `C:\Program Files (x86)\cloudflared\cloudflared.exe`

## Env Alignment Rule

For production, align all of these to the same live local-Supabase stack:
- `VITE_GLOB_API_URL`
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`
- `VITE_SUPABASE_SCHEMA`
- `VITE_SUPABASE_STORAGE_BUCKET`
- `VITE_PROJECT_ID`

Do not assume the old demo anon JWT string is still correct. Prefer the current `Publishable` key from `supabase status`.

## Verification Order

Use this order:
1. `supabase status`
2. `curl http://127.0.0.1:54321/auth/v1/health`
3. `curl http://127.0.0.1:54321/rest/v1/`
4. `Get-Service cloudflared`
5. `curl https://<public-db-host>/auth/v1/health`
6. `curl https://<public-db-host>/rest/v1/`
7. Confirm frontend live build is the latest upload
8. Test login with the known seeded admin account for that project

## Publish Checklist Template

- Local Supabase running
- Public DB hostname routed through Cloudflare tunnel
- `cloudflared` service running
- production env updated to public DB hostname
- production publishable key updated from current local stack
- `dist.zip` rebuilt after env change
- latest `dist.zip` uploaded to hosting
- browser hard-refresh or incognito used after deploy
- seeded admin credentials verified against current local Supabase auth data

## Angel-Specific Evidence Worth Reusing

- Public frontend: `https://admin.interiordesign-angel.com`
- Public tunneled DB: `https://db-xin.aisolo.vip`
- Local Supabase root: `C:\Users\user\Documents\local-supabase`
- Cloudflare tunnel name used: `angel-supabase-tunnel`
- Production zip path: `admin-panel-angel/apps/web-antd/dist.zip`
- Canonical Angel default local admin seed from migration:
  - email: `admin@interiordesignangel.com`
  - password: `123456`

## SOP Pointers Created In This Task

- Project-specific SOP:
  - `C:\Users\user\Desktop\angel-interior\SOP_PUBLISH_ANGEL_ADMIN_VIA_CLOUDFLARE_TUNNEL.md`
- Related reference SOP that inspired the pattern:
  - `C:\Users\user\Desktop\angel-interior\SOP_SETUP_DB_WANI_ON_OTHER_PC.md`

## Retrieval Hints

Search these terms in memory for similar future tasks:
- `vben local supabase cloudflare tunnel publish`
- `dist.zip stale build invalid login credentials`
- `auth health 200 rest 502`
- `cloudflared service install windows administrator`
- `pnpm.cmd build:antd`
