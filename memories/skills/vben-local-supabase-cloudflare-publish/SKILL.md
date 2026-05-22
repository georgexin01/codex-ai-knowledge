---
name: vben-local-supabase-cloudflare-publish
description: Publish a Vben admin frontend that talks to a local Docker Supabase stack through a public Cloudflare Tunnel. Use this for Windows PowerShell projects where the frontend is public but backend/auth/storage stay on the developer PC.
argument-hint: "[project-path] [public-db-host]"
disable-model-invocation: true
user-invocable: false
allowed-tools:
  - Read
  - Grep
  - Glob
  - Bash
---

# Vben Local Supabase Cloudflare Publish

## When to use

Use this when:
1. The frontend is a Vben admin panel.
2. Supabase is running locally in Docker on Windows.
3. The production frontend must call a public hostname that tunnels back to the local Supabase stack.
4. You need a repeatable publish and verification sequence instead of ad hoc deploy debugging.

Do not use this when:
1. The backend is already hosted remotely.
2. The project is not using Supabase or not using a Vben admin frontend.
3. The task is only local development and does not involve a public hostname or production build.

## Inputs / context to gather

1. Confirm the active project authority and the correct frontend app path.
2. Identify the production env file or env injection path for:
   - `VITE_GLOB_API_URL`
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_ANON_KEY`
   - `VITE_SUPABASE_SCHEMA`
   - `VITE_SUPABASE_STORAGE_BUCKET`
   - `VITE_PROJECT_ID`
3. Confirm the local Supabase root and whether `supabase status` works in the current shell.
4. Gather the public DB hostname, the frontend hostname, and the current seeded admin credentials for the target project.
5. Check whether `cloudflared` is already installed and whether the service is running.

## Procedure

1. Confirm the stack authority first.
   - Re-check the active project docs and schema contract before touching deploy settings.
   - Make sure the frontend you are publishing matches the live local Supabase stack.

2. Verify local Supabase health before changing the frontend build.
   - Run `supabase status`.
   - Check `http://127.0.0.1:54321/auth/v1/health`.
   - Check `http://127.0.0.1:54321/rest/v1/`.
   - Do not treat `auth/v1/health = 200` as sufficient proof that `rest` is healthy.

3. Align production env values to the same live local stack.
   - Point the production API/Supabase URLs at the public tunnel hostname, not `localhost`.
   - Prefer the current `Publishable` key from `supabase status`.
   - Do not reuse an old demo JWT string blindly.

4. Configure Cloudflare Tunnel for the public DB hostname.
   - Create or confirm the tunnel and DNS route.
   - Write `C:\Users\<user>\.cloudflared\config.yml` so the public DB hostname proxies to `http://127.0.0.1:54321`.
   - Install the tunnel as a Windows service if the tunnel must survive reboots.

5. Build the frontend with Windows-safe commands.
   - Use `pnpm.cmd`, not bare `pnpm`, when PowerShell policy blocks script shims.
   - Build the production artifact, for example `pnpm.cmd build:antd`.

6. Upload the newest frontend artifact.
   - Publish the latest `apps/web-antd/dist.zip` or the project’s equivalent output.
   - Hard-refresh the browser or use an incognito window before reading login results.

7. Verify the public path end to end.
   - Check the public DB hostname `/auth/v1/health`.
   - Check the public DB hostname `/rest/v1/`.
   - Confirm the live frontend is serving the newest build.
   - Test login with the known seeded admin account for that project.

## Efficiency plan

1. Validate local Supabase and the tunnel before rebuilding the frontend.
2. Search for the six env keys first instead of reading the whole repo.
3. If login fails after deploy, compare local/live bundle hashes before re-debugging auth logic.
4. Stop once you prove the failure belongs to one of these buckets:
   - local Supabase down
   - tunnel/service down
   - env mismatch
   - stale uploaded build
   - wrong credentials for the currently exposed stack

## Pitfalls and fixes

- Symptom: public tunnel returns `502`.
  - Likely cause: local Supabase is stopped or `rest` is not healthy.
  - Fix: rerun `supabase status`, then verify both local health endpoints before checking the public hostname again.

- Symptom: `Invalid login credentials` appears on the live admin.
  - Likely cause: auth is reachable, but the frontend build is stale or the credentials do not match the current local stack.
  - Fix: compare hashed bundle names between local `dist` and the live site, hard-refresh, then retry with the known seeded admin account.

- Symptom: `cloudflared` command is not found even after install.
  - Likely cause: the current shell has not picked up the PATH change.
  - Fix: open a new shell or use `C:\Program Files (x86)\cloudflared\cloudflared.exe` directly.

- Symptom: `cloudflared service install` fails.
  - Likely cause: PowerShell is not truly elevated.
  - Fix: rerun from an Administrator session.

- Symptom: `supabase status` fails in Windows.
  - Likely cause: Docker pipe access is blocked in the current session.
  - Fix: retry from a shell with the needed access level.

## Verification checklist

1. Local `supabase status` is healthy enough for both auth and `rest`.
2. The public tunnel hostname answers both `/auth/v1/health` and `/rest/v1/`.
3. The production env values all point at the same live local-Supabase stack.
4. `cloudflared` is installed and the service state is known.
5. The uploaded frontend artifact is the newest build.
6. Live login works with the expected seeded admin account.
