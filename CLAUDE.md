# CLAUDE.md — Oak Ridges Appliance Repair website

## Your role

You adapt HTML/CSS exported from Claude Design into blocks compatible with the
**sitegen** editor (the client's proprietary AI site builder). You are the last
step of the pipeline: Claude Design (visuals) → **you (code adaptation)** →
sitegen editor (final assembly by the client).

You do NOT know sitegen's internal format. Never guess it. Your first task in
any session where `/sitegen-sample/` exists is to reverse-engineer it (see
Workflow below).

## Project snapshot

- Business: Oak Ridges Appliance Repair — local appliance repair company.
- Service area: ONLY Vaughan and Aurora, Ontario (York Region), Canada. Never
  add other cities. The Oak Ridges community itself is in Richmond Hill, which
  we do NOT serve — that's why the brand name must always appear paired with
  "Vaughan & Aurora".
- Founded: 2022 (use "since 2022" everywhere; never another year).
- Domain: oakridgesappliancerepair.ca
- Strategy: Local SEO lead generation. Conversions = phone calls first, booking
  form second.
- Reference site built on the same template: primefixniagaraappliancerepair.ca

## Placeholders — keep EXACTLY as-is (client will find-and-replace later)

- Vaughan: 240 Chrislea Rd, Unit 11, Vaughan, ON L4L 8V1 — (905) 555-0148
- Aurora: 15483 Yonge St, Unit 5, Aurora, ON L4G 1P3 — (289) 555-0173
- info@oakridgesappliancerepair.ca · Mon–Sat 8 am – 8 pm
Never invent new addresses/phones. 555 numbers are intentional (non-dialable).

## Design tokens (single source of truth)

```css
:root {
  --forest: #2E5636;       /* headings, nav/footer bg, icons, chip borders */
  --forest-deep: #1F3D26;  /* hover states, text on sage */
  --gold: #C29A55;         /* primary CTA bg (with --ink text), lines, stars */
  --gold-deep: #8A6A2F;    /* gold TEXT on cream (a11y); never use --gold for text on cream */
  --bark: #5F482A;
  --cream: #F7F3EA;        /* page background */
  --paper: #FFFFFF;        /* cards */
  --ink: #26261F;          /* body text */
  --sage: #E7EFE7;         /* tinted section bands */
  --border: #E4DCC9;
  --radius-control: 8px;
  --radius-card: 12px;
}
```

- Headings: **Fraunces** 500–600 (Google Fonts). Body/UI: **Figtree** 400/500/600.
- Signature details: 64px×2px gold underline below H1; letterspaced gold
  overline (0.14em, --gold-deep) above section headings; trust chips = cream
  pill with 1px forest border; ridgeline SVG divider between select sections.
- NO photos of technicians or stock people anywhere. Reviews may mention
  technician first names in text.
- No CSS frameworks unless sitegen requires one. Vanilla HTML/CSS + minimal JS.
  Only external dependency: Google Fonts.

## Block contract (why the client can paste blocks into sitegen)

- Every page = vertical stack of full-width `<section>` elements.
- Section ids: `block-01-hero`, `block-02-trustbar`, … stable and sequential.
- No element crosses a section boundary; no negative margins between sections.
- Section padding: 80px top/bottom desktop, 48px mobile.
- Each section must render acceptably when extracted alone. Prefer classes over
  cascade dependencies; if sitegen turns out to require inline styles or
  self-contained blocks, inline the styles per block.

## Site map, titles and H1s (14 pages)

| URL | Title tag | H1 |
|---|---|---|
| / | Oak Ridges Appliance Repair — Vaughan & Aurora | Deep roots. Fast fixes. |
| /vaughan | Appliance Repair in Vaughan, Ontario — Same-Day · Oak Ridges | Appliance Repair in Vaughan |
| /aurora | Appliance Repair in Aurora, Ontario — Same-Day · Oak Ridges | Appliance Repair in Aurora, Ontario |
| /lg | LG Appliance Repair in Vaughan & Aurora · Oak Ridges | LG Appliance Repair in Vaughan & Aurora |
| /samsung | Samsung Appliance Repair in Vaughan & Aurora · Oak Ridges | Samsung Appliance Repair in Vaughan & Aurora |
| /whirlpool | Whirlpool Appliance Repair in Vaughan & Aurora · Oak Ridges | Whirlpool Appliance Repair in Vaughan & Aurora |
| /bosch | Bosch Appliance Repair in Vaughan & Aurora · Oak Ridges | Bosch Appliance Repair in Vaughan & Aurora |
| /kitchenaid | KitchenAid Appliance Repair in Vaughan & Aurora · Oak Ridges | KitchenAid Appliance Repair in Vaughan & Aurora |
| /about-us | About Us · Oak Ridges Appliance Repair | About Oak Ridges Appliance Repair |
| /contact | Contact Us · Oak Ridges Appliance Repair | Contact Oak Ridges |
| /warranty | Warranty · Oak Ridges Appliance Repair | Our Warranty |
| /privacy-policy | Privacy Policy · Oak Ridges Appliance Repair | Privacy Policy |
| /terms-and-conditions | Terms and Conditions · Oak Ridges Appliance Repair | Terms and Conditions |
| /cancellation-policy | Cancellation Policy · Oak Ridges Appliance Repair | Cancellation Policy |

## SEO rules (non-negotiable)

1. **Homepage is keyword-neutral**: brand + "York Region" wording only. No
   "appliance repair in Vaughan"-style phrases in homepage headings.
2. **City pages** use the formal noun in H2s: "Refrigerator Repair in Vaughan"
   (local search data: refrigerator 150/mo vs fridge 80/mo). "Fridge",
   "washing machine" go in body text as synonyms.
3. **Brand pages** use "Fridge" in H3s ("Samsung Fridge Repair" — national
   data: fridge 250/mo vs refrigerator 20/mo). Mix of city-tagged and untagged
   headings, per page copy. Bosch page leads with dishwashers (400/mo).
4. **/vaughan is the priority page** (~1,600 searches/mo vs ~590 Aurora): it
   gets the most internal links; Thornhill and Woodbridge have their own H3
   subsections inside it (Thornhill alone = 150/mo).
5. No brand×city pages. Keys like "samsung appliance repair in Vaughan" exist
   only as anchor texts and H3s inside existing pages.
6. Internal linking: home → both city pages + 5 brand pages; each city page →
   all 5 brand pages (anchor "…appliance repair in {City}"); each brand page →
   both city pages; footer → legal pages. No orphan pages.
7. One H1 per page, exactly as in the table above.

## Structured data

- Every page: `Organization` (name, logo, url) in the footer scope.
- /vaughan and /aurora: one `LocalBusiness` JSON-LD each with that city's NAP
  placeholder, `areaServed`, `openingHoursSpecification` (Mo-Sa 08:00–20:00),
  `telephone`, `priceRange "$$"`. Keep the two locations separate — never merge
  NAP data across cities.
- Reviews rendered on pages must NOT be marked up with AggregateRating schema
  (self-serving reviews violate Google guidelines).
- Canonical tag on every page; OG title/description/image (logo) on every page.

## Conversion furniture (every page)

- Header topbar phone is `tel:` linked; sticky header.
- Mobile: sticky bottom bar, full-width gold "Call (905) 555-0148" button.
- Booking form fields: appliance select, city select (Vaughan/Aurora), phone.
  Microcopy: "Diagnostic fee waived with repair". Forms wired per sitegen's
  mechanism (discover it from the sample; otherwise leave a clearly marked
  `<!-- TODO: sitegen form hook -->`).
- Brand pages have NO reviews block. About Us is text-only (no images/stats).

## Workflow

1. **Reverse-engineer sitegen first.** Read everything in `/sitegen-sample/`
   (client-provided export of a sitegen page/template). Document findings in
   `SITEGEN-NOTES.md`: how blocks are delimited, class naming, inline vs
   stylesheet CSS, image handling, form hooks, JS allowances, anything that
   constrains output. Ask the client to confirm the notes before converting.
2. **Convert page by page**, starting with Home, then /vaughan. Source visuals
   live in `/design-export/` (Claude Design ZIP/HTML). Output to `/dist/{page}/`
   with one file (or fragment set) per block, named `block-NN-name.html`.
3. **Reuse, don't regenerate**: /aurora is a transform of /vaughan; the four
   remaining brand pages are transforms of /lg. Write these as scripted
   find-and-replace transforms where possible so future edits stay cheap.
4. **QA checklist per page** before marking done: block ids sequential and
   self-contained; H1/title match the table; placeholders untouched; tel: links
   work; contrast AA (no --gold text on cream); mobile 390px clean; sticky call
   bar present; schema validates; internal links per rule 6; no technician
   photos; "since 2022" only.

## Commit / output conventions

- Never edit files inside `/design-export/` or `/sitegen-sample/` — read-only
  inputs. All work happens in `/dist/` and `SITEGEN-NOTES.md`.
- Keep a running `CHANGELOG.md` of adaptation decisions so the client can trace
  why converted markup differs from the Claude Design export.
