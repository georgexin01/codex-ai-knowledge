thread_id: 019e6e10-e86a-73a1-9ba8-2119cccef3d7
updated_at: 2026-05-28T10:25:39+00:00
rollout_path: C:\Users\user\.codex\sessions\2026\05\28\rollout-2026-05-28T18-11-10-019e6e10-e86a-73a1-9ba8-2119cccef3d7.jsonl
cwd: \\?\C:\Users\user\Documents\supabase-project-backup-restore
git_branch: main

# Local Angel Interior Supabase setup was audited and repaired before VPS migration

Rollout context: The user wanted their local Supabase project ready to move to VPS and asked to fix missing/incomplete local settings for the `angelinterior` project, including schema naming, storage, policies, config, and backup completeness. The rollout used the local repo at `C:\Users\user\Documents\supabase-project-backup-restore` and the shared local Supabase repo at `C:\Users\user\Documents\local-supabase`.

## Task 1: Fix schema-name mismatch for Angel backup/restore
Outcome: success

Preference signals:
- The user said the schema should be `angelinterior` and asked to “fix this wrong” after backup tooling listed `angel` -> they want the tool and local registry corrected to the real schema, not worked around.
- The user asked “where i will be mocing from local to vps soon.. i want my local database setting and config or policies to be complete” -> they want the local environment made migration-ready, not just explanation.

Key steps:
- Verified `public.project` initially had `schema_name = 'angel'` for the Angel project while the actual DB schema list contained `angelinterior`.
- Updated the local `public.project` row for project `b3e45339-0de0-4073-b03a-7f5468bffe77` to `schema_name = 'angelinterior'` and confirmed the backup prompt then listed `angelinterior`.
- Re-ran `scripts/01-backup-local.sh angelinterior` and confirmed the schema backup now resolved successfully.

Failures and how to do differently:
- The first backup failed with `pg_dump: error: no matching schemas were found` because the backup tool relied on the registry value `angel`, not the real DB schema.
- Future agents should verify both `public.project.schema_name` and `information_schema.schemata` when a backup fails with a schema-not-found error.

Reusable knowledge:
- For this repo, the Angel project’s canonical DB schema is `angelinterior`.
- `public.project` is the lookup source used by `local-backup.bat`; if it is wrong, the backup tool will show the wrong schema and `pg_dump` will fail even when the real schema exists.

References:
- `public.project` row for Angel: `b3e45339-0de0-4073-b03a-7f5468bffe77`
- Key error: `pg_dump: error: no matching schemas were found`
- Verification after fix: `public.project` returned `angelinterior`, and `information_schema.schemata` contained `angelinterior`.

## Task 2: Diagnose and fix storage/policy warnings in local backup
Outcome: success

Preference signals:
- The user asked whether the warnings were “all ok or my local is missing those setting? like no policy?” -> they want warnings distinguished into harmless vs truly missing local configuration.
- The user wanted the local database config and policies “complete” before moving to VPS -> they expect backup tooling to capture all relevant storage/config metadata, not silently skip it.

Key steps:
- Verified the Angel project’s storage bucket was `angel-interior`, not `angelinterior`.
- Verified storage policies were named `angel_interior_*`.
- Verified the bucket existed, there were 449 objects, and the policies existed in `pg_policies`.
- Patched the backup scripts to resolve storage bucket id and policy prefix separately from schema name.
- Patched the backup to copy the shared `local-supabase/supabase/config.toml` when it contains the schema.
- Re-ran the backup successfully and confirmed it now captured:
  - storage bucket `angel-interior`
  - physical storage files from `/mnt/stub/stub/angel-interior`
  - 4 storage policies matching `angel_interior_*`
  - `config.toml`

Failures and how to do differently:
- The earlier warning `No physical storage files found for 'angelinterior'` was false for this project because the real bucket path was `angel-interior`.
- The earlier `No storage policies matching 'angelinterior_*' found` was also false because the real prefix was `angel_interior_*`.
- There was also a shell portability issue while testing a helper directly from PowerShell (`/bin/bash` not found / Git Bash path resolution); rerunning via the actual Git Bash path used by the batch scripts fixed the test path.

Reusable knowledge:
- For the Angel project, three names differ and must be treated independently:
  - DB schema: `angelinterior`
  - storage bucket: `angel-interior`
  - storage policy prefix: `angel_interior`
- The live local storage path for this project was found under `supabase_storage_local-supabase:/mnt/stub/stub/angel-interior`.
- A backup at `local-backups/angelinterior-20260528-182303` was the first verified backup that correctly included storage files and storage policies.

References:
- Storage bucket query result: `angel-interior | angel-interior | t`
- Policy names: `angel_interior_auth_delete`, `angel_interior_auth_insert`, `angel_interior_auth_update`, `angel_interior_public_read`
- Successful backup command: `scripts/01-backup-local.sh angelinterior`
- Successful backup folder: `local-backups/angelinterior-20260528-182303`

## Task 3: Audit local Supabase completeness and improve backup fidelity before VPS migration
Outcome: success

Preference signals:
- The user explicitly framed the next step as migrating from local to VPS and wanted the local setup complete first -> future runs should default to an audit-first, migration-readiness mindset.
- The user wanted missing policies/settings fixed locally, not just identified -> if something is truly absent, update the local setup and the backup tool so it is preserved going forward.

Key steps:
- Audited the local `angelinterior` state in the shared local Supabase repo and the live containers.
- Verified the local Supabase `config.toml` existed at `C:\Users\user\Documents\local-supabase\supabase\config.toml` and already exposed `angelinterior` in `api.schemas`.
- Verified schema privileges existed for `anon`, `authenticated`, and `service_role` on `angelinterior`.
- Verified all 10 tables in `angelinterior` had RLS enabled.
- Verified 43 policies existed in the `angelinterior` schema.
- Verified `public.custom_access_token_hook` existed and matched the hook referenced by `config.toml`.
- Patched the backup script to copy the shared `config.toml` into the backup so future VPS moves include that local config context.
- Verified the newest backup `local-backups/angelinterior-20260528-182503` captured schema/data, auth/public rows, storage metadata, storage files, storage policies, edge functions, and `config.toml`.

Failures and how to do differently:
- The warning about missing `config.toml` was due to the backup script’s lookup logic, not because the local Supabase config was absent.
- The initial helper implementation for storage resolution was too complex for the shell boundary; simplifying it to a smaller resolver and then verifying against the live containers worked.

Reusable knowledge:
- For this project, the local environment is already mostly complete; the main missing pieces were in backup-tool discovery, not the live DB.
- Best verified backup for migration is `local-backups/angelinterior-20260528-182503`.
- Shared local Supabase config already includes `angelinterior` in API exposure, so the migration path should preserve this schema exposure setting.

References:
- `C:\Users\user\Documents\local-supabase\supabase\config.toml`
- `api.schemas = ["public", "graphql_public", "labour", "test_school", "wms", "insurance", "angelinterior", "trash"]`
- RLS-enabled table count: 10
- Policy count in `angelinterior`: 43
- Hook name: `public.custom_access_token_hook`
