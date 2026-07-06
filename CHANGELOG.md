# CHANGELOG — Oak Ridges adaptation decisions

Running log of why converted markup differs from the Claude Design export, so
the client can trace every deviation. Newest first.

## 2026-07-06 — Project setup

- Added `CLAUDE.md` (pipeline contract, design tokens, 14-page site map, SEO
  rules, structured-data and conversion requirements, Workflow).
- Scaffolded the project structure expected by the Workflow:
  `sitegen-sample/` and `design-export/` (read-only inputs), `assets/`
  (logo etc.), and `dist/` (generated output). Each input folder carries a
  placeholder README describing what to drop in.
- **Not started:** no page conversion has happened. Step 1
  (reverse-engineer sitegen → `SITEGEN-NOTES.md`) is blocked until
  `sitegen-sample/` contains a real export. No sitegen format has been guessed,
  per CLAUDE.md.
