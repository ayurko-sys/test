# CHANGELOG — Oak Ridges adaptation decisions

Running log of why converted markup differs from the Claude Design export, so
the client can trace every deviation. Newest first.

## 2026-07-06 — Header nav reverted to match the design

- Confirmed via editor screenshot that the rebuilt header now imports into sitegen.
- The design (states A/B) keeps Vaughan and Aurora as top-level nav items; the
  "Service Area" dropdown I had added was a deviation. Reverted: nav is now
  Home · Vaughan · Aurora · Brands ▾ · About · Contact on desktop, and the same
  as top-level links + Brands accordion on mobile — matching the design exactly.

## 2026-07-06 — Block 01 (Header) rebuilt for sitegen compatibility

- Client reported the first header was **rejected by sitegen**. Root cause: it
  contained constructs absent from the working sample — an inline `<script>`
  (scroll-collapse), custom `data-site-header`/`data-topbar` attributes,
  multi-statement `onclick`, and an extra comment before `<!-- STYLING-HEADER -->`.
- Rebuilt strictly on the sample's skeleton: fixed-height bars (`h-[36px]`/
  `h-[72px]`), single-statement `onclick` toggles, mobile submenus using the
  sample's exact `hidden bg-[#F1EBE0] flex flex-col` pattern, no `<script>`, no
  custom attributes, no leading comment. Dropped the scroll-collapse and the
  hamburger→X / chevron-rotate niceties (all JS-driven) for compatibility.
- **Added a "Service Area" dropdown** (Vaughan, Aurora) on desktop and as a
  mobile accordion, per request — cities now live in a popup mirroring Brands;
  the two top-level city links were consolidated into it. Kept the design's
  clock topbar icon and desktop outline call button.
- Re-verified by offline render: desktop nav + both dropdowns + both mobile
  accordions stack and behave correctly.

## 2026-07-06 — Block 01 (Header) converted

- Extracted the client's Claude Design export into `design-export/` (read-only
  input). Header source: `design-export/export/header-states-src.html` (states A–D).
- Built `dist/home/block-01-header.html` — the site-wide **STYLING-HEADER** —
  matching the design: topbar clock + hours + phone; desktop nav with Home active
  (gold underline) and a Brands dropdown (gold left-accent card); desktop outline
  call button + gold "Book a repair"; mobile centered-phone topbar with bordered
  call/menu buttons and a slide-down menu with a Brands accordion; topbar
  auto-collapses on scroll (design State A note).
- Adaptations per contract: Tailwind utilities + inline-hex fallback on the bars;
  editable strings tagged `data-editable="text"`; logo tagged `data-image-editable`
  and **swapped from the design's acorn to the example project logo** (per request);
  NAP via `{{nap.*}}`; brand/nav hrefs use the CLAUDE.md site-map URLs (`/lg/`,
  `/about-us/`, …), not the design's `/brands/*` placeholders; "Book a repair" →
  `/contact/` (valid on every page, matching the design's link).
- **Verified by offline render** (Tailwind compiled locally since the Play CDN is
  network-blocked here; Chromium): all four states + scroll-collapse match. Fixed
  one render-caught bug — the mobile Brands accordion needed a `flex` toggle to
  stack vertically.
- Kept the 5.1 MB standalone design preview out of git (see `.gitignore`); all
  editable design sources are committed.

## 2026-07-06 — Client decisions folded into the contract

Resolved three CLAUDE.md-vs-sitegen conflicts and updated CLAUDE.md accordingly:

- **Fonts → Lora + Nunito Sans** (was Fraunces + Figtree). The editor's Visual
  Identity drives the deployed site, so tokens now match it. Gold H1
  underline/overline are font-agnostic, unchanged.
- **NAP → tokenize with `{{nap.*}}` site-wide** (supersedes "keep literal 555
  placeholders"). The 555 values remain the canonical reference NAP.
- **Dark sections → remap to brand** `--forest`/`--forest-deep`/`--ink`, never
  Tailwind slate/gray.

Also updated CLAUDE.md to record that sitegen requires Tailwind (Play CDN), the
`data-editable` region tagging, and the real form hook; and defaulted section
padding (80/48px) and radii (8/12px) to the CLAUDE.md contract. Still open before
city pages: per-page SEO/JSON-LD placement and multi-location NAP scheme
(SITEGEN-NOTES.md §12).

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
