---
name: vben-local-supabase-preflight
description: Pre-flight checklist for Vben Admin work backed by local Docker Supabase. Use this before module edits, SQL migrations, drawer forms, storage uploads, or RBAC debugging.
argument-hint: "[project-path]"
disable-model-invocation: true
user-invocable: false
allowed-tools:
  - Read
  - Grep
  - Glob
  - Bash
---

# Vben Local Supabase Pre-flight

## When to use

Use this when:
1. The project is a Vben Admin panel using a local Docker Supabase stack.
2. The task touches SQL, migrations, forms, drawers, uploads, storage URLs, or role permissions.
3. You want to avoid the Angel/PowerShell failure modes that already cost debugging time.

Do not use this when:
1. The project is a static website or small app that does not use Vben Admin.
2. The database is not the local Docker Supabase stack.
3. The task is purely presentational and does not touch forms, storage, or database behavior.

## Inputs / context to gather

1. Confirm the working repo and active admin app path.
2. Find the local migration folder and inspect the highest existing migration number.
3. Identify whether the task touches:
   - SQL or migrations
   - drawer-driven forms
   - RLS or role permissions
   - storage uploads or preview URLs
4. Search for these high-signal handles first:
   - `defineExpose`
   - `formApi`
   - `permissions`
   - `FOR INSERT`
   - `getStorageUrl`
   - `.from('attachments')`
   - `safe_delete_active_attachment`
   - `updatedAt`

## Procedure

1. Confirm this is really local Docker Supabase.
   - Check for local Docker/Supabase commands, local ports like `54323`, or repo docs that name the local stack.

2. If SQL must run, prepare a file-based path.
   - Put the SQL in a migration file or standalone `.sql` file.
   - Use `docker cp` plus `psql -f`.
   - Do not use inline `psql -c` on PowerShell for camelCase-heavy SQL.

3. If the task edits a drawer form, verify `formApi` exposure before wiring behavior.
   - Open the form component.
   - Confirm `formApi` is exposed via `defineExpose`.
   - If missing, add it before debugging parent drawer actions.

4. If the task touches permissions or insert flows, check dual-grant coverage.
   - Verify the RLS policy exists.
   - Verify the role also has the matching `permissions` row.
   - Treat policy plus permission row as one checklist item.

5. If the task touches uploads or file previews, inspect the storage path format.
   - Stored object paths must not start with `/`.
   - If preview/download URLs show `//`, normalize the stored path before URL generation.

6. If the task changes live tables, prefer corrective migrations.
   - Inspect the highest migration number first.
   - Add the next numbered migration.
   - Prefer `ALTER` over DROP+CREATE when rows already exist.

7. Validate the auth/data bridge if user management is involved.
   - Check `auth.users`, `public.user`, and `{schema}.users`.
   - If any layer is missing or unsynced, login/admin flows can fail even when the schema looks mostly complete.

## Efficiency plan

1. Start with `rg` on the high-signal handles instead of broad repo reads.
2. Read the migration directory before reading application code when the task smells schema-related.
3. If the task touches uploads, search `getStorageUrl` and attachment/store usage before opening UI files.
4. If the task touches create/edit drawers, inspect the form component before the parent drawer.
5. Stop escalating once the relevant failure mode is confirmed and a focused fix path is clear.

## Pitfalls and fixes

- Symptom: SQL behaves differently from the file version or camelCase identifiers break.
  - Likely cause: inline `psql -c` quoting on PowerShell.
  - Fix: switch to `docker cp` plus `psql -f`.

- Symptom: drawer UI opens but save/edit logic does not respond correctly.
  - Likely cause: `formApi` was not exposed in `defineExpose`.
  - Fix: add the exposure in the form component first.

- Symptom: `INSERT` returns 403 even though an RLS policy exists.
  - Likely cause: missing matching `permissions` row for that role/action.
  - Fix: verify the dual grant, not just the policy.

- Symptom: uploaded file URLs 404 or contain `//`.
  - Likely cause: stored object path begins with `/`.
  - Fix: normalize paths before calling `getStorageUrl()`.

- Symptom: a fast schema reset would wipe real data or drift history.
  - Likely cause: using DROP+CREATE on live tables.
  - Fix: write the next numbered corrective `ALTER` migration instead.

## Verification checklist

1. SQL changes were applied from a file, not inline PowerShell SQL.
2. New migrations use the next valid number and preserve live data where required.
3. Drawer forms expose `formApi` when parent drawers depend on it.
4. RLS-sensitive flows have both the policy and the matching `permissions` row.
5. Storage paths do not start with `/`, and preview/download URLs no longer contain `//`.
6. If user management changed, `auth.users`, `public.user`, and `{schema}.users` still line up.
