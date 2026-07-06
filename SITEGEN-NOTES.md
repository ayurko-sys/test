# SITEGEN-NOTES.md — reverse-engineered sitegen format

**Status:** DRAFT — awaiting client confirmation before any page conversion.
**Sources:** `sitegen-sample/home-template.html` (a real exported Home page) +
`sitegen-sample/visual-identity-settings.md` (editor Colors/Fonts panel).
**Date:** 2026-07-06.

> Read this top-to-bottom, then confirm/correct §12 (open questions) and §13
> (conflicts with CLAUDE.md). I will not convert Home until those are settled.

---

## 1. Document shell & dependencies

- Export is a **complete HTML document** (`<!DOCTYPE html>` → `</html>`) with a
  `<head>` containing only: charset, viewport, `<title>Page Preview</title>`,
  and **`<script src="https://cdn.tailwindcss.com"></script>`**.
- **Sitegen requires Tailwind** (loaded via the Play CDN). This overrides the
  CLAUDE.md line "No CSS frameworks unless sitegen requires one" — it does.
  All styling is Tailwind utility classes; there is no separate stylesheet.
- **No Google Fonts `<link>` in the export.** Fonts are applied by the
  deployment template from the Visual Identity settings (see §5), not per-block.
- `<title>` is a generic placeholder in the export ("Page Preview"); the real
  per-page `<title>`/meta/canonical/OG/JSON-LD are **not** in the block stream —
  they are almost certainly injected by the deployment template / page settings,
  not editable inside a block. **Open question §12.1.**

## 2. Block delimiting & page structure

The body is a flat, sequential stack. Two comment conventions:

- **Site-wide chrome**, introduced by a banner comment and a marker:
  ```html
  <!-- ═══ SITE-WIDE HEADER (edits apply globally to this project) ═══ -->
  <!-- STYLING-HEADER -->
  <header ...>…</header>
  ```
  Edits here apply to **every page** in the project (global header). A matching
  `STYLING-FOOTER` almost certainly exists for the global footer, though this
  export renders the footer as a normal numbered block (see note below).
- **Per-page blocks**, each introduced by:
  ```html
  <!-- BLOCK {N}: {TYPE} (ID: {uuid}) -->
  <section|header|footer ...>…</section>
  ```
  - `{N}` = 1-based sequential index.
  - `{TYPE}` = block category from a fixed taxonomy. Seen in this sample:
    `NAVIGATION, HERO, TRUST, FEATURE, TESTIMONIAL, CONVERSION`. (Both the
    contact-form section **and** the footer are typed `CONVERSION`.)
  - `{uuid}` = editor-assigned block id (e.g. `dc4c8edd-ea37-4f91-b448-…`).
    **We do not invent these**; the editor mints them on import. Our own
    `block-NN-name.html` file names in `/dist/` are just our filing scheme.
- **Each block is exactly one top-level element** (`<header>` / `<section>` /
  `<footer>`), self-contained, no element spanning two blocks. This matches the
  CLAUDE.md block contract.
- **Quirk:** the sample emits the header twice — once as the global
  `STYLING-HEADER`, then again as `BLOCK 1: NAVIGATION` with identical markup.
  Likely an export artifact (global chrome + the page's own first block). Need
  to confirm whether a converted page should include the NAVIGATION block or
  rely solely on the global header. **Open question §12.2.**

## 3. Editable-region system (`data-editable`) — critical

The editor makes regions editable by tagging them. Our converted blocks **must**
carry these attributes or the client can't edit the text/images in sitegen.

- **Text slots:** `data-editable="{slot}"` where slot ∈:
  - `headline` — the section's main heading (H1/H2)
  - `subheadline` — the supporting sub-heading / secondary heading
  - `body` — paragraph / small text
  - `text` — short standalone strings (top-bar text, testimonial author, etc.)
  - `cta` — buttons and link CTAs
  - `section` — placed on some whole `<section>` wrappers
  - `true` — generic "this text is editable" (used throughout the footer)
- **Repeatable items:** `data-editable="items.{i}.{field}"`, 0-based, e.g.
  `items.0.title`, `items.0.description` on card grids. The index ties the DOM
  node to an array entry in the editor's model. Keep indices contiguous per grid.
- **Images:** `data-image-editable="true"` on any `<img>` the client may swap.
- **Noise to NOT copy:** the generator leaked `data-editable="body"` onto SVG
  `<path>` elements and even produced malformed tags in the footer social icons
  (`…z"/ data-editable="body">`). These are artifacts — we tag **real text/CTA
  nodes**, never SVG paths, and we emit valid markup.

## 4. Color system

Three layers coexist; use them in this order of preference:

1. **Semantic tokens (shadcn-style), wired to Visual Identity** — preferred for
   body blocks. Seen: `primary`, `primary-foreground`, `secondary`, `accent`,
   `background`, `foreground`, `muted-foreground`, `border`, `destructive`
   (as `bg-primary`, `text-primary`, `bg-primary/10`, `border-accent`,
   `text-foreground`, `bg-background`, …). Mapping (from §Visual Identity):
   `primary=#2E5636`, `secondary=#1F3D26`, `accent=#C29A55`,
   `background=#F7F3EA`, `foreground=#26261F`.
2. **Arbitrary hex utilities** — for brand tokens the editor doesn't expose
   (`--gold-deep`, `--bark`, `--paper`, `--sage`, `--border`). Seen:
   `border-[#E4DCC9]`, `bg-[#F7F3EA]`, `bg-[#E4DCC9]`, `bg-[#F1EBE0]`,
   `hover:text-[#2E5636]`, `border-[#E4DCC9]/50`.
3. **Inline `style` hex** — used as a hard fallback on the **global header** for
   brand-critical fills: `style="background-color:#2E5636;color:#F7F3EA"`,
   `style="background-color:#C29A55;color:#26261F"`. The header carries **both**
   the semantic class **and** the inline hex ("belt-and-suspenders"), so the
   brand color survives even if the token isn't resolved in a given context.
   → **Rule:** for global chrome and any must-not-break brand fill, emit the
   semantic class **and** an inline hex fallback.

**Off-brand palette in the sample (important):** the body blocks lean on stock
Tailwind grays — `bg-slate-900` for every dark section (hero, coverage, form,
footer), plus `slate-50/100/200/300/600/700` and `gray-50/200/600/900`. The
brand has **no** slate; the darkest brand colors are `--ink #26261F` and
`--forest-deep #1F3D26`, and dark bands should be `--forest #2E5636`. Whether to
keep the generic slate or remap dark sections to brand tokens is **§13 / §12.3**.

**Accessibility — the sample already respects one CLAUDE.md rule and breaks
others:**
- ✅ Gold `#C29A55` is only ever a **background** (with `#26261F` ink text),
  never gold text on cream — matches "never use --gold for text on cream".
  Emphasis text uses `text-primary` (forest), not gold. Good.
- ❌ **Real contrast bugs to fix, not copy:** (a) the Testimonial section
  sub-heading and author sub-labels use `text-slate-200` on white / near-white
  cards — near-invisible; (b) the CONVERSION form heading uses
  `text-foreground` (`#26261F`) on `bg-slate-900` — dark-on-dark. CLAUDE.md QA
  requires AA, so these get corrected during conversion.

## 5. Fonts — CONFLICT

- Visual Identity panel sets **Heading = Lora**, **Body = Nunito Sans**, and the
  panel states these feed the deployment template → the **live site will render
  in Lora/Nunito Sans**.
- CLAUDE.md design tokens mandate **Fraunces** (headings) / **Figtree** (body),
  with signature details (64px gold H1 underline, 0.14em gold overline) tuned to
  those faces.
- These disagree. Blocks themselves don't set `font-family` (good — no conflict
  at block level), but the rendered result depends entirely on the editor
  setting. **Decision needed — §13.1.**

## 6. NAP & templating (`{{nap.*}}`)

- Sitegen interpolates NAP via **`{{ }}` (Handlebars/Mustache-style)** tokens.
  Confirmed fields from the global header:
  - `{{nap.phone_tel}}` → dialable value for `href="tel:…"` (digits, e.g. `+19055550148`)
  - `{{nap.phone}}` → display phone, e.g. `(905) 555-0148`
  - `{{nap.business_name}}` → e.g. used in logo `alt`
- **Body blocks hardcode NAP** instead of tokenizing — the HERO uses
  `href="tel:+19055550148"` and literal `(905) 555-0148`. That's the
  Claude-Design output before adaptation. **Our job:** replace every hardcoded
  phone/name/address/email with the matching `{{nap.*}}` token so the client's
  central NAP drives the whole site. This supersedes the "keep literal 555
  placeholders" note in CLAUDE.md — sitegen's native mechanism is `{{nap.*}}`.
- **Likely-but-unconfirmed fields** we'll need (naming to confirm): `nap.email`,
  `nap.address` / `nap.address_full`, `nap.city`, `nap.postal_code`,
  `nap.hours`. **Open question §12.4.**
- **Two locations problem:** CLAUDE.md keeps Vaughan and Aurora NAP strictly
  separate (distinct addresses, phones, and one `LocalBusiness` JSON-LD each).
  A single flat `nap.*` namespace can't hold both. Need to know how sitegen
  models multi-location NAP (e.g. `nap.vaughan.*` / `nap.aurora.*`, or a second
  location object, or per-page NAP). **This blocks /vaughan and /aurora — §12.5.**

## 7. Forms — the "form hook" (resolves the CLAUDE.md TODO)

The CONVERSION block contains the real mechanism (no more
`<!-- TODO: sitegen form hook -->` guesswork):

- **Form element:** `<form id="contact-form" data-contact-form
  cr-form-attach-retry="false" data-cr-no-capture novalidate>`. The
  `data-contact-form` attribute is what the editor/runtime binds to.
- **Fields:** each input carries `data-field="{name}"` (`name`, `phone`,
  `email`) and a sibling error `<p data-error="{name}">`. Consent checkbox uses
  `data-terms`. Submit button `data-submit-btn`. Success panel
  `data-success-message` (a sibling of the form).
- **Phone input:** `data-phone-mask="true" data-raw-value="" data-country-code="+1"`;
  an inline script masks to `+1 (XXX) XXX-XXXX` and validates 10 digits.
- **Endpoint:** POST JSON to the literal placeholder **`'__FORM_ENDPOINT__'`**,
  which the deployment replaces. We keep this token verbatim.
- **Tracking:** CallRail (`data-cr-no-capture` + manual `CallTrk.captureForm`,
  deliberately once per submit) and a GA4 `dataLayer.push({event:'generate_lead'})`.
- **JS:** one self-contained IIFE per form; it auto-initializes **all**
  `form[data-contact-form]` on the page, so duplicate forms are fine.
- **Booking form gap:** CLAUDE.md's booking form needs an **appliance select**,
  a **city select (Vaughan/Aurora)**, a phone, and the microcopy "Diagnostic fee
  waived with repair." The sample is a generic name/phone/email/terms contact
  form. To build the booking form we extend this same pattern: add
  `<select data-field="appliance">` and `<select data-field="city">`, and add
  those keys to the `payload` object in the script. **Confirm the editor accepts
  extra `data-field`s / selects — §12.6.**

## 8. JavaScript allowances

- **Inline `onclick`** is used (mobile menu + submenu toggles via
  `classList.toggle('hidden')`) → inline handlers are allowed.
- **Inline `<script>`** is allowed (the form IIFE lives inside the block).
- External runtime deps observed: Tailwind CDN, `api.ipify.org` (client IP),
  CallRail `swap.js` (implied by `CallTrk`). Minimal JS, vanilla — matches
  CLAUDE.md.

## 9. Images

- Hosted absolute URLs on the project's Supabase bucket
  (`…supabase.co/storage/v1/object/public/project-images/…`). The editor uploads
  and rewrites `src`; our `assets/logo.png` becomes such a URL on import.
- Swappable images get `data-image-editable="true"`; non-hero images use
  `loading="lazy"`. Logo is `.webp`.
- For conversion we reference the design-export images and tag them
  `data-image-editable="true"`; the client re-points them in the editor.

## 10. Layout / spacing conventions

- Inner container everywhere: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8`.
- Arbitrary values are common: `h-[36px]`, `h-[72px]`, `text-[15px]`,
  `rounded-[8px]`, `h-[400px]`, `max-h-[calc(100vh-108px)]`.
- **Section padding in the sample is `py-24` (96px)** for major sections and
  `py-12` (48px) for the trust strip — **not** the CLAUDE.md "80px desktop /
  48px mobile". Reconcile: use `py-20 md:py-20` (80px) per contract, or match the
  sample's `py-24`? **§13.2.**
- Corner radii in the sample (`rounded-xl`, `rounded-2xl`, `rounded-3xl`) are
  looser than the CLAUDE.md tokens (`--radius-control 8px`, `--radius-card 12px`,
  seen correctly only as `rounded-[8px]` on buttons). **§13.3.**
- Anchor mismatch bug: header CTA → `#booking`, hero CTA → `#book`, but the
  CONVERSION section has **no** matching `id`. We'll add a real `id` (e.g.
  `id="booking"`) and make both CTAs point to it.

## 11. Reconciliation with the CLAUDE.md block contract

| CLAUDE.md contract | Sitegen reality | Action on conversion |
|---|---|---|
| Full-width `<section>` stack | ✅ flat stack of `<section>`/`<header>`/`<footer>` | keep |
| `id="block-01-hero"` sequential ids | Editor uses UUIDs + `<!-- BLOCK N: TYPE -->` comments; sections have no such id | our `/dist` file names carry the scheme; emit the `BLOCK N` comment for traceability |
| No frameworks | Tailwind CDN required | use Tailwind utilities |
| Prefer classes; inline if required | Tokens + arbitrary hex + inline-hex fallback on chrome | follow §4 layering |
| Keep literal 555 placeholders | Native `{{nap.*}}` interpolation | tokenize NAP (§6), pending §12.5 |
| `<!-- TODO: sitegen form hook -->` | Real `data-contact-form` + `__FORM_ENDPOINT__` | use §7 mechanism |
| 80px/48px section padding | Sample uses `py-24`/`py-12` | decide §13.2 |
| Fraunces / Figtree | Editor set to Lora / Nunito Sans | decide §13.1 |
| Per-page title/canonical/OG/JSON-LD | Not in block stream | confirm where these live §12.1 |

## 12. Open questions (need answers to proceed accurately)

1. **Head/SEO:** Where do per-page `<title>`, meta description, canonical, OG
   tags, and JSON-LD (`Organization`, `LocalBusiness`) go — page settings, a
   template, or a special block? CLAUDE.md requires them on every page.
2. **NAVIGATION duplication:** Should a converted page include the `BLOCK N:
   NAVIGATION` block, or only the global `STYLING-HEADER`? Same question for a
   `STYLING-FOOTER` vs the `CONVERSION` footer block.
3. **Dark sections:** keep stock `slate-900` or remap to brand `--forest` /
   `--ink` / `--forest-deep`?
4. **NAP fields:** confirm exact token names beyond phone/business_name
   (email, address, city, postal, hours).
5. **Multi-location NAP (blocks /vaughan, /aurora):** how does sitegen hold two
   separate NAPs (Vaughan vs Aurora) for content + the two `LocalBusiness`
   schemas?
6. **Booking form:** does the editor accept extra `data-field` selects
   (appliance, city) added to the `data-contact-form` pattern + payload?

## 13. Conflicts with CLAUDE.md that need a client decision

1. **Fonts:** editor = Lora + Nunito Sans; CLAUDE.md = Fraunces + Figtree.
   Change the editor's Visual Identity to Fraunces/Figtree, or update the design
   tokens to Lora/Nunito Sans? (Affects the H1 underline / overline styling.)
2. **Section padding:** 80/48px (CLAUDE.md) vs `py-24`/`py-12` (sample).
3. **Radii:** enforce `--radius-control 8px` / `--radius-card 12px`, or keep the
   sample's looser `rounded-2xl/3xl`?
4. **NAP representation:** confirm we replace literal 555 placeholders with
   `{{nap.*}}` tokens site-wide (recommended, per §6) — this changes the
   CLAUDE.md "keep placeholders exactly as-is" instruction.

---

*Next step after sign-off: convert Home (`/design-export/` → `/dist/home/`),
block by block, applying §3 editable tags, §4 color layering, §6 NAP tokens, and
§7 form mechanism, then run the CLAUDE.md QA checklist.*
