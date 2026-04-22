# personal-data/

This folder is a placeholder. It mirrors the structure of the personal version of this plugin.

When a user first runs any of the four skills (`failure-pattern-guard`, `business-fit-score`, `kill-criteria-enforce`, `founder-check`), the first-run interview produces two files:

- `failure-patterns.md` — the user's personal failure patterns (built from their venture history)
- `business-criteria.md` — the user's weighted evaluation criteria

These files are written to `~/.claude/founder-discipline-public/` on the user's machine (NOT inside the plugin folder — plugins are read-only at runtime).

This folder exists as documentation of where the files conceptually belong in the plugin's architecture. If you want to pre-populate the plugin with example data before install (e.g., for a shared team version), drop your files here and copy them to `~/.claude/founder-discipline-public/` manually.
