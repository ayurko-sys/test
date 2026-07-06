# CHANGELOG — Oak Ridges adaptation decisions

Running log of why converted markup differs from the Claude Design export, so
the client can trace every deviation. Newest first.

## 2026-07-06 — Step 1: reverse-engineered sitegen format

- Client provided a real sitegen export + the editor's Visual Identity panel.
  Saved verbatim to `sitegen-sample/home-template.html` and
  `sitegen-sample/visual-identity-settings.md` (read-only inputs); removed the
  empty-folder placeholder.
- Wrote `SITEGEN-NOTES.md` documenting: Tailwind-CDN document shell;
  `<!-- BLOCK N: TYPE (ID: uuid) -->` delimiting + `STYLING-HEADER` global
  chrome; the `data-editable` / `data-image-editable` editable-region vocabulary
  (incl. `items.{i}.{field}`); the 3-layer color system (shadcn semantic tokens
  + arbitrary hex + inline-hex fallback); `{{nap.*}}` NAP interpolation; and the
  real form hook (`data-contact-form` + `__FORM_ENDPOINT__` + CallRail/GA4).
- **Still not converting.** Surfaced conflicts with CLAUDE.md needing client
  sign-off (see SITEGEN-NOTES §12–§13): fonts (editor Lora/Nunito Sans vs
  Fraunces/Figtree), NAP tokenization vs literal 555 placeholders, multi-location
  NAP for Vaughan/Aurora, where per-page SEO/JSON-LD lives, section padding, and
  dark-section palette (stock slate vs brand).

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
