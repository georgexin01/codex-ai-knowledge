# Reusable workflow extraction: project handoff docs and database Markmap

Generic reusable preferences extracted from a project planning workflow, without project-specific paths or schema:

- For database planning that needs a human-viewable mindmap in VS Code, prefer a Markdown-backed Markmap file such as `DATABASE_MARKMAP.md` over binary `.xmind` files.
- Keep `DATABASE.md` as the canonical schema/auth/RLS contract, `TABLE_STRUCTURE.md` as the quick table overview, and `DATABASE_MARKMAP.md` as the visual mindmap source.
- Include Supabase/Postgres-ready names and types in the mindmap: schema-qualified table names, snake_case columns, `uuid`, `text`, `int`, `bigint`, `boolean`, `date`, `timestamptz`, and `jsonb`.
- Treat visual/mindmap edits as proposed schema changes; sync back to the canonical database Markdown before implementation.
- For Vben/Supabase admin projects, require explicit user approval before translating database/mindmap changes into admin modules, migrations, stores, routes, or permissions.
- A reusable root handoff stack should include a small entrypoint, one-screen blueprint, master plan, database contract, crosswalk, inventory docs, and explicit sync/update rules.

Created skills:

- `skills/markdown-database-mindmap/SKILL.md`
- `skills/project-handoff-doc-stack/SKILL.md`
- `skills/claude/database-markmap-sync/skill.md`
