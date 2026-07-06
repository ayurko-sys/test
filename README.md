# Oak Ridges Appliance Repair — site build workspace

Adapts HTML/CSS from **Claude Design** into blocks for the client's proprietary
**sitegen** editor. Pipeline:

```
Claude Design (visuals)  →  code adaptation (here)  →  sitegen editor (final assembly)
```

The operational contract lives in [`CLAUDE.md`](./CLAUDE.md) and loads
automatically when you run `claude` from this directory.

## Layout

| Path | Role | Status |
|---|---|---|
| `CLAUDE.md` | Pipeline contract: tokens, block rules, 14-page map, SEO/schema rules | ✅ present |
| `sitegen-sample/` | **Input (read-only):** the real sitegen export + Visual Identity settings | ✅ provided |
| `design-export/` | **Input (read-only):** unpacked Claude Design export (visuals) | ⛔ empty — needed for Step 2 |
| `assets/` | Shared assets (`logo.png`, …) | ⛔ empty |
| `dist/` | **Output:** converted `block-NN-name.html` per page | — nothing generated yet |
| `SITEGEN-NOTES.md` | Step 1 output: reverse-engineered sitegen format (client confirms before converting) | ✅ drafted — **awaiting sign-off** |
| `CHANGELOG.md` | Running log of adaptation decisions | ✅ present |

`appliance-repair-seo-competitor-research.md` is prior Australia-market SEO
research, unrelated to this Canadian project — left in place, untouched.

## How to run

1. Drop your exports into the input folders above (see each folder's README).
   `sitegen-sample/` is the blocker — even the raw 5-page template sitegen gave
   you works as a sample.
2. From this directory, run `claude`. Then, first message:

   > Read CLAUDE.md. Start with step 1 of the Workflow: reverse-engineer the sitegen
   > format from /sitegen-sample/ and write SITEGEN-NOTES.md. Don't convert anything yet.

3. Confirm the notes, then convert page by page:

   > Proceed to step 2: convert the Home page from /design-export/ into /dist/home/

   Order: Home → /vaughan (priority) → the rest. `/aurora` is built as a
   transform of `/vaughan`; the four remaining brand pages as transforms of
   `/lg` — cheaper and consistent, per the Workflow.

## Current status

**Step 1 done, awaiting sign-off.** The sitegen format is reverse-engineered from
the client's export into [`SITEGEN-NOTES.md`](./SITEGEN-NOTES.md). Before Home is
converted, the client needs to resolve the conflicts/open questions in that file's
§12–§13 (fonts, NAP tokenization + multi-location, per-page SEO placement, spacing,
dark-section palette). No page conversion and no format guessing has happened.
