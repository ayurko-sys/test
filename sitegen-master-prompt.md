# Sitegen Master Prompt — Fraser Appliance Repair

**Використання:** вставити промпт нижче в Sitegen одним повідомленням. Плейсхолдери в `[КВАДРАТНИХ ДУЖКАХ]` замінити реальними даними до або після генерації (Claude Code потім допилює кожен блок).

---

```
Create a 15-page local service website for "Fraser Appliance Repair" — a locally owned appliance repair company founded in 2020, serving exactly three cities in Metro Vancouver, BC, Canada: Surrey, Delta, and White Rock. Core positioning: trusted local experts + SAME-DAY appliance repair. Tone: professional, warm, plain-spoken, neighbourly; written like a local technician-owner speaks, no corporate fluff. Use Canadian English spelling (neighbourhood, licenced/licence, centre, colour). Currency CAD.

GLOBAL RULES (apply to every page):
- NO photos of technicians anywhere on the site. No stock-photo "smiling repairman" imagery. Use photos/illustrations of appliances, tools, service vans, kitchens, and local scenery instead.
- Sticky click-to-call phone button on mobile; phone number [PHONE] visible in header on every page with "Same-Day Service" label and today's availability ("Open today until [8pm]").
- Every page ends with a booking block: 4-field form (Name, Phone, Appliance type, City) + "or call [PHONE]" + callback promise ("We call back within 15 minutes, 7 days a week").
- Trust strip used site-wide (text badges, no images): Licensed & Insured · [90-Day / 6-Month] Parts & Labour Warranty · Same-Day Appointments · Locally Owned & Operated Since 2020 · Service Call Fee Waived With Repair.
- Footer: NAP ([BUSINESS NAME, CITY, BC, PHONE, EMAIL]), Areas We Serve (Surrey, Delta, White Rock), Brands We Repair (Samsung, LG, Bosch, Whirlpool, KitchenAid), links to Privacy Policy, Terms & Conditions, Cancellation Policy, Warranty.
- Appliances we service (use this list wherever services are shown): refrigerators & freezers, washing machines, dryers, dishwashers, ovens, stoves & cooktops, range hoods.
- Internal linking: Home links to all 3 city pages and all 5 brand pages; each city page links to all 5 brand pages; each brand page links to all 3 city pages.
- Schema: LocalBusiness (HomeAndConstructionBusiness) JSON-LD on Home with areaServed = Surrey, Delta, White Rock; Service schema on city pages; FAQPage schema where FAQs exist.

PAGES:

1) HOME — "/"
Keep the homepage NEUTRAL of commercial keywords: do NOT stuff "appliance repair" phrases into H1. H1 is brand-led, e.g. "Fraser Appliance Repair — Your Local Appliance Experts in Surrey, Delta & White Rock". Mention the brand, the three cities, and real neighbourhood names naturally.
Sections in order:
- Hero promo: brand promise, same-day angle ("Book before noon — we're usually at your door the same day"), phone + booking CTA.
- About teaser: locally owned since 2020, why neighbours call us first (3-4 sentences, link to About Us).
- Services grid WITHOUT city binding: the 7 appliance types, each with a 1-2 sentence description of common problems we fix (not linked to any city).
- Service area: the three cities with 1-2 lines each naming real neighbourhoods — Surrey (Whalley/City Centre, Guildford, Fleetwood, Newton, Cloverdale, South Surrey), Delta (North Delta, Ladner, Tsawwassen), White Rock (Uptown, East Beach, West Beach, Five Corners) — each linking to its city page + a note "usually on-site within hours".
- Reviews: 4-6 customer testimonials, each attributed to a first name + neighbourhood (e.g. "Harpreet, Newton" / "Margaret, White Rock").
- Benefits of working with us: same-day & weekend appointments, upfront written quotes, service call fee waived with repair, [WARRANTY] on parts & labour, repair-first honesty ("if replacing is smarter, we'll tell you"), background-checked local technicians.
- Something local: a short "We know local homes" block — e.g. we service everything from 1970s split-levels in North Delta and basement-suite laundry sets in Newton to compact stacked washer-dryers in Surrey City Centre and White Rock condo towers.
- Brands strip: Samsung, LG, Bosch, Whirlpool, KitchenAid (+ "and most major brands"), linking to brand pages.
- Final booking block.

2) CITY PAGE — "/appliance-repair-surrey/"
H1: "Appliance Repair in Surrey, BC". Target keywords naturally: appliance repair surrey, fridge/refrigerator repair surrey, washer/washing machine repair surrey, dryer repair surrey, dishwasher repair surrey, oven/stove repair surrey.
Sections: promo hero with same-day promise for Surrey; services + location block (each of the 7 appliance types with a Surrey-specific sentence); "Surrey neighbourhoods we serve" listing all six town centres + sub-areas (Fraser Heights, Bolivar Heights, Panorama Ridge, Sullivan Heights, Clayton Heights, Grandview Heights, Morgan Creek, Ocean Park, Crescent Beach); local-expertise paragraph mentioning real Surrey specifics (basement suites with second kitchens and laundry sets, 2005-2025 Clayton/Grandview townhomes whose builder-grade appliances fail on the same schedule, compact 24" appliances and stacked laundry in City Centre condo towers, busy multigenerational households); brand + local block: short subsections like "Samsung appliance repair in Surrey", "LG appliance repair in Surrey", "Bosch appliance repair in Surrey", "Whirlpool appliance repair in Surrey", "KitchenAid appliance repair in Surrey" linking to brand pages; reviews block with 3-4 Surrey-attributed testimonials; FAQ (3-5 Surrey-named questions: how fast can you come to Surrey today, do you charge a service call fee, which areas of Surrey do you cover, do you repair appliances in basement suites/condos); booking form.

3) CITY PAGE — "/appliance-repair-delta/"
H1: "Appliance Repair in Delta, BC". Keywords: appliance repair delta bc, appliance repair north delta / ladner / tsawwassen, dishwasher repair delta.
CRITICAL local angle: treat Delta as THREE distinct communities separated by Burns Bog — North Delta (Annieville, Nordel, Scottsdale, Sunshine Hills: mostly 1965-1990 split-levels with original aging appliances and basement suites), Ladner (historic fishing village, rancher homes, many long-time homeowners), Tsawwassen (the sunniest corner of Metro Vancouver: mid-century ranchers in Beach Grove and Pebble Hill alongside brand-new homes at Tsawwassen Shores and Southlands coming off builder warranty). Give each community its own subsection with same-day coverage note.
Include: promo hero; services + Delta block; the three community subsections; brand + local block (Samsung/LG/Bosch/Whirlpool/KitchenAid appliance repair in Delta with links); a differentiator line "same-day AND weekend appointments across Delta" (competitors here work Mon-Fri); reviews with Delta attributions (e.g. "Dave, Ladner", "Simran, North Delta"); FAQ (do you serve Ladner and Tsawwassen or just North Delta; weekend availability; older-home appliances); booking form.

4) CITY PAGE — "/appliance-repair-white-rock/"
H1: "Appliance Repair in White Rock, BC". Keywords: appliance repair white rock, appliance repair south surrey.
Local angle: serve the whole Semiahmoo Peninsula — White Rock AND South Surrey (Ocean Park, Crescent Beach, Sunnyside, Semiahmoo Town Centre). Speak to the local reality: one of the oldest communities in BC — patient, unrushed service, exact arrival windows, clear phone booking (no app required), honest repair-vs-replace advice for people on fixed incomes; condo/strata specialization (about half of White Rock homes are condos: stacked and ventless laundry in closets, water-shutoff coordination, leak-sensitive stratas, buildings from 1970s-90s walk-ups on Marine Drive hillside to new Uptown towers on Johnston Road). Mention Uptown vs the Beach, East Beach/West Beach, Five Corners naturally.
Include: promo hero; services + White Rock block; neighbourhood/peninsula subsection; brand + local block (5 brands in White Rock, linked); premium note (we also service built-in and premium appliances common in hillside and waterfront homes); reviews with White Rock/South Surrey attributions; FAQ (do you serve South Surrey too; can you work in strata buildings; seniors discount [IF TRUE]); booking form.

5-9) BRAND PAGES — "/samsung-appliance-repair/", "/lg-appliance-repair/", "/bosch-appliance-repair/", "/whirlpool-appliance-repair/", "/kitchenaid-appliance-repair/"
H1 pattern: "[Brand] Appliance Repair in Surrey, Delta & White Rock" — ALWAYS tie the brand to all three cities. NO reviews/testimonials block on brand pages.
Sections per brand page:
- Promo hero: same-day [Brand] repair across Surrey, Delta & White Rock; not affiliated with [Brand] disclaimer line.
- Appliance types we fix for this brand, with brand-specific common issues:
  * Samsung: fridges (cooling/ice maker issues), washers, dryers, dishwashers, ranges — mention how common Samsung packages are in newer Surrey townhomes and condos.
  * LG: fridges (compressor concerns), washers (front-load), dryers, dishwashers, ranges.
  * Bosch: EMPHASIZE dishwashers (quiet German-engineered units, error codes like E15) + ovens/cooktops, washers/dryers.
  * Whirlpool: fridges, washers, dryers, dishwashers, ranges — the workhorse brand in established Surrey and North Delta family homes.
  * KitchenAid: dishwashers, fridges, ranges/wall ovens, mixers excluded — premium kitchen suites.
- Service area block: Surrey, Delta, White Rock each one line with link to city page (e.g. "Samsung washer repair in Newton or a fridge in Tsawwassen — same-day when booked before noon").
- Recent jobs block: 3 short anonymized case entries per page — format "Problem → What we found → How we fixed it → Area" (e.g. "Samsung fridge not cooling in Fleetwood — failed evaporator fan, replaced on the spot from van stock"). Realistic, no customer names, no reviews.
- Booking form.

10) ABOUT US — "/about-us/"
TEXT-ONLY page: no images, no statistics counters, no visual embellishments. Company story told in first person plural: started in 2020 by a local technician [FOUNDER STORY]; named after the Fraser River delta communities we grew up around; why we stayed a three-city company on purpose (short drive times = honest same-day promises); how we work (written quotes, fee waived with repair, warranty on parts & labour, respect for your home); licensed & insured, [CERTIFICATIONS IF REAL: Red Seal technicians, Technical Safety BC gas licence, WorkSafeBC]. End with a soft CTA line and phone. Keep it human and specific, around 400-600 words.

11) CONTACT US — "/contact/"
Phone (click-to-call), email, hours [HOURS incl. weekends], service area list (3 cities + note on neighbourhoods), booking form, map of the service area (Surrey-Delta-White Rock), response-time promise. No physical walk-in address shown [SAB — service-area business].

12) PRIVACY POLICY — "/privacy-policy/" — standard privacy policy for a Canadian small business website (PIPEDA-aware): what we collect via forms/calls, how used, no selling data, cookies/analytics, contact for requests.

13) TERMS & CONDITIONS — "/terms-and-conditions/" — service terms: quotes/estimates, payment, parts availability, liability limits, service area.

14) CANCELLATION POLICY — "/cancellation-policy/" — plain-language: free cancellation/rescheduling up to [X hours] before the appointment window, how to cancel (call/text), late-cancellation fee [$X IF ANY], no-show policy, same-day booking notes.

15) WARRANTY — "/warranty/"
Plain-language warranty page: [90-day / 6-month / 12-month] warranty on PARTS AND LABOUR, what's covered, what's not (new unrelated faults, customer damage, pre-existing conditions), how to claim (call us, priority re-visit), transparent tone. This page is a trust asset — write it generously.
```

---

## Плейсхолдери для заміни
| Плейсхолдер | Що вставити |
|---|---|
| `[PHONE]` | реальний трекінг/основний номер |
| `[EMAIL]` | robота email |
| `[HOURS]` / `[8pm]` | реальні години (вікенди — важливо для Delta-гепу) |
| `[90-Day / 6-Month]` | фінальний термін гарантії (рекомендація: 6 міс — довше за ринок) |
| `[BUSINESS NAME, CITY, BC ...]` | NAP; місто бази визначає map pack |
| `[FOUNDER STORY]` | 2-3 факти від власника для сторітелінгу |
| `[CERTIFICATIONS IF REAL]` | лише реальні сертифікати (Red Seal / TSBC / WorkSafeBC) |
| `[IF TRUE]` seniors discount | підтвердити у власника |
| `[X hours]`, `[$X IF ANY]` | правила скасування |

## Наступні кроки процесу
1. Прогнати промпт у Sitegen → отримати каркас 15 сторінок.
2. Claude design: брендбук (палітра, типографіка, вигляд елементів: trust strip, booking form, review cards, brand chips) → спакувати для Claude Code.
3. Claude Code: допил кожного блоку по чеклісту з `fraser-appliance-repair-seo-research.md` (розділи 2-3: EEAT-текст, локальні хуки, schema JSON-LD, перелінковка).
4. Паралельно: GBP (категорія Appliance Repair Service + hide address + 3 service areas), цитати Tier 1 (yellowpages.ca, 411.ca, HomeStars, Yelp, BBB), відгуки 2-5/міс.
