# NotebookLM Registry

Purpose: lightweight registry for user-provided NotebookLM paths so Codex can route research quickly without repeated path parsing.

## Active Notebook Paths

- `https://notebooklm.google.com/notebook/a2ba712a-1285-4f23-bedf-a6b866f32fc3`
- `https://notebooklm.google.com/notebook/f3e15792-0237-4b42-a2da-aa64c7243252`

## Usage Notes

- Treat links as mission context pointers, not guaranteed directly-readable sources.
- When a user shares new NotebookLM links during any task, append them here automatically (deduplicated).
- If direct access is unavailable, ask user for summary/export/excerpts from the same notebook.
- After extraction, store only compact findings, not full notebook dumps.
