# SEO Competitor Research — Appliance Repair (Melbourne · Sydney · Canberra)

**Дата:** 2026-07-01
**Ніша:** appliance repair / fridge · washing machine · dishwasher · oven · cooktop · dryer · rangehood repair
**Ринки:** Melbourne, Sydney, Canberra (Австралія)
**Мета:** знайти конкурентів, у яких **informational content реально приносить organic traffic** (не просто «є блог»), розібрати які саме сторінки працюють, і скласти контент-стратегію для нового (greenfield) проєкту.
**Джерела даних:** Ahrefs API v3 (SERP Overview `country=au`, Batch Analysis, Site Explorer → Top Pages, Keywords Explorer). Трафік — оцінка Ahrefs, org. пошук.

---

## 0. Методологія та ключові застереження

1. **Дискавері.** Реальні австралійські SERP зібрані через Ahrefs `serp-overview` з `country=au` по 14 city-keyword-групах + 14 informational/error-code seed-запитах (проблеми приладів + бренд-error-codes). Це надійніше за парсинг Google, бо дає саме австралійську видачу.
2. **Кваліфікація.** ~55 доменів прогнані через Batch Analysis (worldwide + AU) → organic traffic, keywords, traffic value, top country. Далі топ-конкуренти розібрані по Top Pages (`country=au`), кожна сторінка класифікована: informational / brand-repair / service / e-commerce / parts.
3. **Виключено** маркетплейси й агрегатори (Airtasker, Oneflare, hipages, Yellow Pages, ProductReview, Reddit, Facebook, YouTube, JustAnswer, Quora, region.com.au) — вони не прямі service-competitors.
4. **Що вважаємо «informational»:** сторінки з problem/troubleshooting/how-to/error-code/cost/advice інтентом (напр. *fridge not cooling*, *bosch dishwasher error codes*, *how to clean oven*). **Brand-repair landing** (напр. */pages/bosch-appliance-repairs*) і **city/suburb service** сторінки рахуємо окремо — це комерційні, не informational.

### ⚠️ Застереження до даних
- **Це low-traffic ніша.** Справжні локальні repair-сервіси мають ~150–2 300 organic visits/міс з Австралії. «Великі» цифри (industrykitchens 85k, appliancesonline 408k) належать сайтам, що **не є** repair-сервісами (e-commerce/retail), чий блог випадково ранжується по appliance-проблемах.
- **Нерелевантний / не-австралійський трафік позначено ⚠.** Напр. `rightwhitegoods.com.au` має 11.6k загального трафіку, але лише **27% з Австралії** — решта це глобальні DIY-запити. `industrykitchens.com.au` має 31k AU-трафіку, але це **кулінарний контент** (unit conversions, «schooner glass size»), а не appliance repair.
- **Volume vs traffic.** У таблицях `volume` = AU-обсяг запиту; сторінка часто отримує більше трафіку, ніж volume головного ключа, бо ранжується по десятках додаткових ключів.
- **Canberra — тонкі дані.** Менший ринок; **жоден локальний гравець Canberra не робить informational content** (лише service + brand + warranty сторінки). Оскільки informational-запити національні, це не проблема — контент, зроблений для Melbourne/Sydney, автоматично збирає Canberra-трафік.

---

## 1. Головні organic competitors по містах

### Melbourne
| Domain | DR | AU organic traffic | Модель | Коментар |
|---|---|---|---|---|
| **thefridgeguy.com.au** | 4 | ~1,238 | **Problem pages + service** | ⭐ Найкращий кейс problem-сторінок (fridge leaking/not cooling) |
| **melbournemetrorefrigeration.com.au** | 5 | ~701 | **Blog + suburb + brand** | ⭐ Блог = ~50% трафіку |
| appliancesrepairsonline.com.au | 9 | ~572 | Service + brand pages | 0 informational |
| theovenrepairman.com.au | 2 | ~702 | Service (oven) | Нішевий, oven-only |
| legacyrepairs.com.au | 2 | ~209 | Service | 0 informational |
| localwashingmachinerepairs.com.au | 1 | ~340 | Service (washing machine) | 0 informational |
| appliancemedic.com.au | 0 | ~201 | Service | 0 informational |
| appliancefixer.com.au | 8 | ~244 | Gas + oven guides | 1 relevant page (oven not heating) |
| *(також ранжуються)* theovenguy, ovenfixer, asappliances, metroappliancerepair, arriveontime, ultimateappliances | 0–7 | <200 | Service | Service-only |

### Sydney
| Domain | DR | AU organic traffic | Модель | Коментар |
|---|---|---|---|---|
| **theapplianceguys.com.au** | 26 | ~17,099 | **Retailer + repair + blog** | ⭐ Лідер; error-codes + cleaning-guides блог |
| **sydneyappliance.com.au** | 24 | ~1,123 | Service + parts + деякі problem pages | Бренд-трафік homepage домінує |
| **agw.com.au** (All General Whitegoods) | 10 | ~1,144 | Brand-repair + parts | 1 brand-issues сторінка |
| **bestrepairs.com.au** | 13 | ~799 | Service + /articles/ (brand landing) | Кілька problem-статей |
| eplappliances.com.au | 16 | ~207 | Service | 0 informational |
| abco.com.au | 42 | ~349 | Service | DR42, але тонкий контент |
| fridgerepairs.com.au | 8 | ~? | Service (fridge) | Service-only |
| sydneywashingmachinerepair.com.au / sydneyfridgerepair.com.au (Parrahills) | 2–3 | <250 | Service | Service-only |
| *(також)* aquawashingmachines, stovedoc, totalappliancerepaircentre, stevesmithstoverepairs, smartappliance, sydneyapplianceservices, sydneydomesticappliance | 0–8 | <150 | Service | Service-only |

### Canberra
| Domain | DR | AU organic traffic | Модель | Коментар |
|---|---|---|---|---|
| **gbrs.com.au** (Ginger Beard Repair Service) | 4 | ~636 | Service (.html сторінки) | Лідер Canberra; 0 informational |
| **maynerandcochran.com.au** | 9 | ~560 | Brand-repair + LG/IKEA warranty | 0 problem-content |
| tech1repairs.com.au | 28 | ~163 | Multi-city service | DR28, service-only |
| fyshwickappliancesrepair.com.au | 0 | ~? | Service | Service-only |
| actmajesticservices.com.au | 0 | ~? | Service | Service-only |
| dbsapplianceservice.com.au (SMEG spec.) | 0 | ~? | Brand service | Service-only |
| ccappliancerepairs.com.au / renewedappliances.com.au | 0 | <100 | Service | Service-only |

> **Висновок по містах:** У всіх трьох містах локальні SERP по «X repair [city]» на 90% складаються з **service/city landing pages** низькоавторитетних сайтів (DR 0–9) + директорій + Google PAA. Informational content у цих SERP майже не з'являється — він живе окремо, у **національних** problem/error-code запитах.

---

## 2. Конкуренти, у яких informational content РЕАЛЬНО працює

Тільки жменя гравців пробилась у informational-видачу і отримує з неї трафік. Ось вони, від найсильнішого:

| # | Domain | Тип гравця | Informational-модель, що працює | AU informational traffic |
|---|---|---|---|---|
| 1 | **rightwhitegoods.com.au** | Content-first lead-gen | DIY problem guides + інтерактивний «appliance age checker» tool | ~1,270 (⚠ сайт лише 27% AU) |
| 2 | **theapplianceguys.com.au** | Appliance retailer | Cleaning how-to + brand error-code блоги | ~850+ |
| 3 | **thefridgeguy.com.au** | Fridge repair (Melb) | Fridge **problem pages** (leaking, not cooling) | ~315 (25% сайту) |
| 4 | **melbournemetrorefrigeration.com.au** | Fridge repair (Melb) | **Blog** (noise, temp, leaking, cost, not cooling) | ~351 (≈50% сайту) |
| 5 | **prestigerepairs.com.au** | Repair + parts (Adelaide) | Brand-repair pages (двигун) + error-code блоги | ~97 блог / brand-repair ~1,032 |
| 6 | **whybuy.com.au** | Appliance rental | Appliance-ownership advice (regas cost, moving, temp) | ~300 (⚠ 65% не-AU) |
| 7 | **sydneyappliance.com.au** | Repair (Syd) | Кілька problem + error-code сторінок | ~56 |
| 8 | **bestrepairs.com.au** | Repair (Syd) | /articles/ (переважно brand-landing) + пара problem | ~26 |

**Позначено як нерелевантні / оманливі:**
- ⚠ **industrykitchens.com.au** — 31k AU-трафіку, але це кулінарний/hospitality контент (unit conversions, cafe names). Єдина релевантна сторінка: `/Blog/dishwasher-not-draining/` (89). **Не** appliance-repair informational competitor.
- ⚠ **appliancesonline.com.au** (retailer, 408k) — має `/article/` контент по проблемах приладів, але це роздрібний магазин, не сервіс.
- Manufacturer-сайти (Bosch, Samsung, LG, Miele, Westinghouse, Electrolux, Fisher & Paykel, Haier) домінують у error-code видачі — це «стеля» видачі, не прямі конкуренти, але вони показують попит.

---

## 3. Таблиця 1 — Огляд конкурентів (competitor-level)

> Traffic = оцінка Ahrefs, organic. «Informational traffic» = сума AU-трафіку problem/how-to/error/cost сторінок (без brand-repair та service landing).

| Competitor domain | City focus | Est. organic traffic (WW) | Organic traffic AU | Total organic KW | Informational приносить трафік? | Est. informational traffic (AU) | % informational | Top informational URL | Traffic URL | Main keyword URL | Page type | Notes (чому корисний) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **thefridgeguy.com.au** | Melbourne | 1,296 | 1,238 | 278 | **Yes** | ~315 | **~25%** | /why-is-my-fridge-leaking-water/ | 226 | why is my fridge leaking water | appliance problem page | ⭐ DR4, а одна problem-сторінка = 18% сайту. Еталон ROI problem-сторінок |
| **melbournemetrorefrigeration.com.au** | Melbourne | 749 | 701 | 210 | **Yes** | ~351 | **~50%** | /blog/fridge-noise-fix/ | 127 | fridge making loud buzzing noise | blog / troubleshooting | ⭐ Блог = половина трафіку при DR5; кластер fridge-проблем |
| **theapplianceguys.com.au** | Sydney (national) | 19,870 | 17,099 | 4,358 | **Yes** | ~850+ | ~5% | /blogs/oven/9-best-methods-for-cleaning-your-oven | 278 | how to clean oven naturally | blog how-to + error codes | Retailer; cleaning-guides + brand error-codes — сильний вторинний канал. Traffic value ~$5,967/mo |
| **rightwhitegoods.com.au** | National (Perth) | 11,593 | 3,142 | 1,173 | **Yes** | ~1,270 | **~40%** | /blog/washing-machine-not-draining | 385 | how to fix washing machine not draining | blog troubleshooting + tool | Найчистіша content-модель + «appliance age checker». ⚠ 73% трафіку не-AU |
| **prestigerepairs.com.au** | Adelaide (national brands) | 2,256 | 2,196 | 785 | Yes (помірно) | ~97 (блог) | ~4% (блог) | /blogs/news/...fisher-paykel...error-codes | 46 | fisher and paykel dishdrawer troubleshooting | error-codes blog | **Brand-repair landing = двигун (~47%)**. Модель бренд-сторінок для реплікації |
| **whybuy.com.au** | National (rental) | 4,926 | 1,714 | 1,734 | Yes | ~300 | ~18% (AU) | /blog/fridge-repair-guide-basic-diagnosis-and-repair-cost/ | 113 | how much does it cost to regas a fridge | blog advice/cost | Rental-бренд; appliance-ownership контент. ⚠ 65% не-AU |
| **sydneyappliance.com.au** | Sydney | 1,149 | 1,123 | 524 | Yes (мало) | ~56 | ~5% | /fridge-leaking-water-inside/ | 24 | fridge leaking water | appliance problem page | Branded homepage домінує; кілька problem/error сторінок працюють. Traffic value ~$600/mo |
| **bestrepairs.com.au** | Sydney | 808 | 799 | 205 | Yes (мало) | ~26 | ~3% | /articles/dryer-not-heating-up/ | 14 | dryer not heating up | article / problem | /articles/ = здебільшого brand-service landing (LG, ILVE, Smeg repairs Sydney) |
| **appliancefixer.com.au** | Melbourne | 261 | 244 | 129 | Частково | ~60 (переважно gas) | ~25% | /10-reasons-why-your-oven-is-not-heating/ | 24 | oven not heating up | blog troubleshooting | Контент здебільшого про gas-compliance; 1 реплікабельна oven-сторінка |
| **agw.com.au** | Sydney | 1,156 | 1,144 | 330 | Мінімально | ~21 | ~2% | /what-are-the-most-common-bosch-washing-machine-repair-issues/ | 21 | common faults with bosch washing machine | brand FAQ | Service/brand/parts; brand-repair pages (Bosch 141, LG 67) |
| **maynerandcochran.com.au** | Canberra | 560 | 560 | 181 | Ні (brand/warranty) | ~0 problem | ~0% | /lg-warranty-refrigerators/ | 17 | lg warranty australia | brand / warranty page | Brand-repair + LG/IKEA warranty; problem-контенту немає |
| **appliancesrepairsonline.com.au** | Melbourne | 593 | 572 | 155 | **No** | 0 | 0% | — | — | — | service + brand | Чиста service-модель. Бенчмарк «як НЕ отримувати info-трафік» |
| **gbrs.com.au** | Canberra | 637 | 636 | 81 | **No** | 0 | 0% | — | — | — | service page | Лідер Canberra; 100% service .html сторінки |
| **abco.com.au** | Sydney | 358 | 349 | 70 | **No** | 0 | 0% | — | — | — | service page | DR42, але тонкий контент — недовикористаний потенціал |
| **eplappliances.com.au** | Sydney | 207 | 207 | 61 | **No** | 0 | 0% | — | — | — | service page | Service-only |
| **theovenrepairman.com.au** | Melbourne | 769 | 702 | 102 | **No** | 0 | 0% | — | — | — | service page (oven) | Нішевий oven-сервіс, лише service |
| **tech1repairs.com.au** | Canberra | 163 | 163 | 59 | **No** | 0 | 0% | — | — | — | service page | DR28; multi-city service |
| ⚠ **industrykitchens.com.au** | National (commercial) | 85,546 | 31,696 | 13,893 | Технічно так, але **нерелевантно** | ~89 relevant | <1% relevant | /Blog/dishwasher-not-draining/ | 89 | dishwasher not draining | blog | ⚠ 31k AU — кулінарний контент, НЕ repair. Лише 1 релевантна сторінка |

---

## 4. Таблиця 2 — Найкращі informational-сторінки (best pages)

> Traffic = AU organic (Ahrefs). Volume/KD = Ahrefs Keywords Explorer, `country=au`. Майже всі ключі — **національні** (не прив'язані до міста), тому релевантні для Melbourne, Sydney і Canberra одночасно. Priority = наскільки варто реплікувати (трафік × низький KD × комерційна близькість).

| # | Competitor | URL | Page title (скор.) | Page type | Est. AU traffic | Main keyword | KW volume (AU) | KD | Position | City relevance | Тема для реплікації | Priority |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | rightwhitegoods | /blog/how-to-clean-dryer-vent | How to clean a dryer vent | how-to | 456 | how to clean dryer vent | 1,100 | 22 | 5 | National (Melb/Syd/Cbr) | Dryer-vent cleaning guide | **High** |
| 2 | rightwhitegoods | /blog/washing-machine-not-draining | WM not draining — 4 DIY fixes | troubleshooting | 385 | how to fix washing machine not draining | 200* | 0 | 6 | National | Washing machine not draining | **High** |
| 3 | theapplianceguys | /blogs/oven/9-best-methods-for-cleaning-your-oven | 9 methods to clean your oven | how-to | 278 | how to clean oven naturally | 1,800 | 11 | 11 | National | Oven cleaning guide | **High** |
| 4 | thefridgeguy | /why-is-my-fridge-leaking-water/ | Fridge leaking water? | appliance problem | 226 | why is my fridge leaking water | 200 | 1 | 2 | National (Melb) | Fridge leaking water | **High** |
| 5 | theapplianceguys | /blogs/stoves/how-to-clean-your-glass-cooktop-or-stove-top | Clean a glass cooktop | how-to | 218 | how to clean glass stovetop | 1,000 | 2 | 9 | National | Glass cooktop cleaning | **High** |
| 6 | rightwhitegoods | /blog/dishwasher-not-draining | Dishwasher not draining | troubleshooting | 150 | dishwasher not draining | 900 | 4 | 5 | National | Dishwasher not draining | **High** |
| 7 | rightwhitegoods | /blog/washing-machine-leaking | Washing machine leaking | troubleshooting | 147 | washing machine leaking from underneath | 150 | 1 | 5 | National | Washing machine leaking | **High** |
| 8 | theapplianceguys | /blogs/oven/...oven-settings-symbols-and-functions... | Oven symbols explained (AU) | guide | 146 | fan forced oven symbol | 1,200 | 1 | 5 | National | Oven symbols/settings guide | **High** |
| 9 | melbournemetro | /blog/fridge-noise-fix/ | Fridge making noise — fix | troubleshooting | 127 | fridge making loud buzzing noise | 70 | 4 | 4 | National (Melb) | Fridge making noise | **High** |
| 10 | whybuy | /blog/fridge-repair-guide-basic-diagnosis-and-repair-cost/ | Fridge repair cost guide | advice/cost | 113 | how much does it cost to regas a fridge | 70 | 0 | 1 | National | Fridge repair/regas cost | Medium |
| 11 | theapplianceguys | /blogs/dishwashers/miele-dishwasher-error-codes | Miele dishwasher error codes | error codes | 111 | miele dishwasher f11 | 600 | 0 | 10 | National | Miele dishwasher error codes | **High** |
| 12 | industrykitchens | /Blog/dishwasher-not-draining/ | Dishwasher not draining | troubleshooting | 89 | dishwasher not draining | 900 | 4 | 6 | National | (валідує тему) | **High** |
| 13 | thefridgeguy | /fridge-not-cold-but-freezer-ok/ | Fridge not cooling, freezer OK | appliance problem | 78 | fridge not cooling but freezer working | 80 | 2 | 4 | National (Melb) | Fridge not cooling (freezer ok) | **High** |
| 14 | melbournemetro | /blog/freezer-temperature/ | Ideal freezer temperature | advice | 72 | ideal freezer temperature | 250 | 20 | 8 | National | Ideal fridge/freezer temp | Medium |
| 15 | theapplianceguys | /blogs/repair/fisher-paykel-dishwasher-error-codes | F&P dishwasher error codes | error codes | ~69 | fisher and paykel dishwasher f30 error | 250 | 0 | 5 | National | F&P dishwasher error codes | **High** |
| 16 | melbournemetro | /blog/fridge-leaking-water/ | Fridge leaking water inside | appliance problem | 66 | fridge leaking water inside | 70 | ~0 | 4 | National (Melb) | Fridge leaking water | **High** |
| 17 | melbournemetro | /blog/fridge-repair-cost/ | Fridge repair cost / regas | advice/cost | 63 | cost to regas fridge | 90 | ~0 | 2 | National | Fridge repair/regas cost | Medium |
| 18 | prestigerepairs | /blogs/news/your-fisher-paykel-dishwashers-language-of-error-codes | F&P error codes | error codes | 46 | fisher and paykel dishdrawer troubleshooting | 150 | 0 | 7 | National | F&P dishwasher error codes | **High** |
| 19 | rightwhitegoods | /blog/fridge-isnt-cooling | Fridge not cooling — 11 fixes | troubleshooting | 39 | fridge not cold enough | 100 | 4 | 7 | National | Fridge not cooling | **High** |
| 20 | theapplianceguys | /blogs/dishwashers/common-bosch-dishwasher-error-codes | Bosch dishwasher error codes | error codes | ~34 | bosch dishwasher error codes | 300 | 0 | 6 | National | Bosch dishwasher error codes | **High** |
| 21 | melbournemetro | /blog/fridge-not-cooling/ | Why is my fridge not cooling | troubleshooting | 23 | why is my fridge not cold | 150 | ~0 | 6 | National | Fridge not cooling | **High** |
| 22 | sydneyappliance | /fridge-leaking-water-inside/ | Fridge leaking water inside | appliance problem | 24 | fridge leaking water | 250 | 0 | 6 | National (Syd) | Fridge leaking water | **High** |
| 23 | sydneyappliance | /electrolux-washing-machine-error-codes/ | Electrolux WM error codes | error codes | 24 | electrolux washing machine error codes | 30 | 0 | 7 | National | Electrolux WM error codes | Medium |
| 24 | appliancefixer | /10-reasons-why-your-oven-is-not-heating/ | Oven not heating — 10 reasons | troubleshooting | 24 | oven not heating up | 200 | 0 | 6 | National | Oven not heating | **High** |
| 25 | bestrepairs | /articles/dryer-not-heating-up/ | Dryer not heating up | troubleshooting | 14 | dryer not heating up | 70 | 2 | 5 | National (Syd) | Dryer not heating | Medium |

\* «how to fix washing machine not draining» показує AU-volume 200, але глобально 167k — сторінка додатково збирає трафік з десятків супутніх ключів (тому 385 visits).

---

## 5. Висновок: який тип контенту працює найкраще

**Рейтинг за реальною ефективністю в цій ніші (Австралія):**

1. **Appliance PROBLEM pages** (fridge not cooling / leaking / making noise, washing machine not draining / spinning / leaking, dishwasher not draining / not cleaning, oven not heating, dryer not heating).
   - **KD 0–4** — найлегші для ранжування ключі в ніші.
   - Приносять найбільше трафіку локальним сервісам: `thefridgeguy` — 226 visits з ОДНІЄЇ сторінки при DR4; `melbournemetro` блог = 50% сайту при DR5.
   - Близькі до покупки: людина зі зламаним приладом = потенційний клієнт.

2. **Brand ERROR-CODE pages** (Bosch dishwasher, Fisher & Paykel DishDrawer, LG / Samsung washing machine, Miele dishwasher, Westinghouse oven, Electrolux).
   - **KD 0** майже завжди — конкуренція мінімальна (крім самих виробників).
   - Дуже висока намір-специфічність; `theapplianceguys` і `prestige` стабільно збирають цей трафік. Miele f11 — 600 volume, KD0.

3. **Brand REPAIR landing pages** (bosch/lg/samsung/smeg/miele/electrolux/asko/fisher&paykel appliance repair + [city]).
   - **KD 0–12**, комерційний інтент → найкраща конверсія.
   - Це справжній двигун `prestigerepairs` (~47% трафіку) і присутній у `appliancesrepairsonline`, `agw`, `maynerandcochran`, `sydneyappliance`. Traffic potential «samsung fridge repairs» = 5,300; «bosch dishwasher repair» = 2,600.

4. **Cost / advice pages** (fridge repair cost, cost to regas a fridge, is it worth repairing X, ideal fridge/freezer temperature).
   - KD 0–20; ловлять pre-decision аудиторію (`whybuy`, `melbournemetro`).

5. **Cleaning / maintenance how-to** (clean oven, clean glass cooktop, clean dryer vent, oven symbols).
   - Найбільший volume (1,000–1,800 AU), але **нижчий комерційний інтент** і трохи вищий KD (11–22). Добре для top-of-funnel + збору посилань (`theapplianceguys`, `rightwhitegoods`).

6. **Interactive tools** (appliance age checker у `rightwhitegoods` — 96 visits + лінкбілдинг-магніт).

7. **City / suburb service landing pages** — обов'язкові для конверсії, але **найважчі** (appliance repair melbourne KD31, appliance repairs sydney KD45). Ранжуються повільно; їх треба підпирати informational-кластером + локальними сигналами (GBP, suburb pages як у melbournemetro).

**Що НЕ працює / оманливе:**
- «Блог заради блогу» без problem/brand-фокусу (більшість service-сайтів мають про/контакти сторінки з 0 трафіку).
- Гнатися за high-volume cleaning/generic-запитами як за основною стратегією — багато трафіку нерелевантне і не конвертує (кейс `industrykitchens`, `rightwhitegoods` з 73% не-AU).

---

## 6. Рекомендації: які сторінки будувати першими (greenfield content plan)

Оскільки проєкт **новий** (без бенчмарку власного домену), стратегія — швидко зайняти **low-KD informational-кластери**, які великі гравці ще не закрили в Австралії, і звести їх воронкою до brand-repair та city-service сторінок.

### 🟢 Хвиля 1 (0–3 міс) — Problem pages + Error codes (KD 0–4, швидкий трафік)
Створити по одній сильній сторінці на кожну проблему (національний таргетинг, приклади в дужках — конкуренти, яких перевершуємо/копіюємо):

- **Fridge:** `fridge not cooling` (KD0), `fridge leaking water` (KD0/1), `fridge making noise` (KD4), `freezer not freezing` (KD0), `fridge not cooling but freezer working` (KD2) — *еталон: thefridgeguy, melbournemetro*
- **Washing machine:** `washing machine not draining` (KD0–2), `washing machine not spinning` (KD2), `washing machine leaking` (KD1) — *еталон: rightwhitegoods*
- **Dishwasher:** `dishwasher not draining` (KD4), `dishwasher not cleaning` (KD0)
- **Oven / cooktop:** `oven not heating up` (KD0), `cooktop not working`
- **Dryer:** `dryer not heating` (KD2)
- **Brand error codes** (KD0, окрема сторінка на бренд): `bosch dishwasher error codes` (300), `lg washing machine error codes` (250), `samsung washing machine error codes` (70), `miele dishwasher error codes` (600!), `fisher and paykel dishwasher error codes` (250), `westinghouse oven error codes`, `electrolux washing machine error codes`.

> Формат: заголовок «[Problem]? Causes & How to Fix (Australian Guide)», симптоми → причини → DIY-кроки → «коли викликати майстра» + CTA на brand-repair/city-service. Додати FAQ-схему (Google показує PAA по всіх цих запитах).

### 🟡 Хвиля 2 (3–6 міс) — Brand-repair hubs + Cost/advice (комерційна конверсія)
- **Brand-repair landing** (KD 0–12) на кожен бренд × сервіс: `bosch appliance repair`, `lg washing machine repair`, `samsung fridge repairs`, `smeg dishwasher repair`, `miele/electrolux/westinghouse/asko/fisher & paykel repairs` — з версіями під Melbourne / Sydney / Canberra. *Еталон: prestigerepairs, appliancesrepairsonline.*
- **Cost/advice:** `fridge repair cost` / `cost to regas a fridge`, `is it worth repairing a [appliance]`, `ideal fridge/freezer temperature`, `how long do [appliances] last`.
- **Warranty helper** сторінки (як maynerandcochran: `lg warranty australia` 350 vol) — ловлять брендовий трафік.

### 🔵 Хвиля 3 (6–12 міс) — City/suburb service + tools + cleaning
- **City service pages:** `appliance repair Melbourne/Sydney/Canberra` + **suburb pages** (модель melbournemetro: fridge repairs werribee/craigieburn…). KD вищий (31–45) — підпирати внутрішніми лінками з problem-сторінок + GBP.
- **Interactive tool:** «Appliance age / model checker» (лінкбілдинг-магніт, як rightwhitegoods).
- **Cleaning/maintenance how-to** (top-of-funnel, для трафіку й посилань): `how to clean your oven`, `how to clean a glass cooktop`, `oven symbols explained`, `how to clean a dryer vent`.

### Архітектура та внутрішня перелінковка (воронка)
```
Problem page (fridge not cooling)  ──►  Brand-repair page (samsung fridge repairs Sydney)  ──►  City service page (fridge repair Sydney) ──► Book/Contact CTA
Error-code page (bosch dishwasher e15) ─►  Brand-repair page (bosch appliance repair)      ──►  City service page
```
- Кожна informational-сторінка мусить мати чіткий CTA + лінк на відповідну brand-repair / city-service сторінку.
- Кластеризувати по parent-topic (Ahrefs): «fridge not working», «washing machine not draining», «[brand] service centre».

### Чому це спрацює для нового сайту
- **KD 0–4** на problem/error-code означає, що навіть сайт з DR<10 реально виходить у топ (доведено: thefridgeguy DR4, melbournemetro DR5, rightwhitegoods DR6).
- **Конкуренти слабкі:** локальні сервіси майже не роблять informational; лише 6–8 гравців на всю країну. Canberra — взагалі відкрите поле.
- **Трафік близький до грошей:** проблема приладу → виклик майстра, на відміну від чисто cleaning-запитів.
- **Один добрий hub тягне багато:** traffic potential brand-repair та problem-кластерів = 1,000–5,300 visits/mo з набору ключів однієї сильної сторінки.

---

## 7. Шорт-лист «скопіювати/покращити» в першу чергу

| Пріоритет | Сторінка для створення | Модель-конкурент | KW volume (AU) | KD |
|---|---|---|---|---|
| 1 | Fridge leaking water — causes & fix | thefridgeguy (226 visits) | 200 | 1 |
| 2 | Washing machine not draining — DIY fixes | rightwhitegoods (385) | 350 | 0–2 |
| 3 | Bosch dishwasher error codes | theapplianceguys / prestige | 300 | 0 |
| 4 | Miele dishwasher error codes (f11 …) | theapplianceguys (111) | 600 | 0 |
| 5 | Fridge not cooling (+ «freezer still works») | thefridgeguy / melbournemetro | 350 | 0–2 |
| 6 | Fisher & Paykel dishwasher/DishDrawer error codes | theapplianceguys / prestige | 250 | 0 |
| 7 | Dishwasher not draining | rightwhitegoods / industrykitchens | 900 | 4 |
| 8 | Fridge making noise | melbournemetro (127) | 70 | 4 |
| 9 | Oven not heating up | appliancefixer | 200 | 0 |
| 10 | LG / Samsung washing machine error codes | (виробники — обійти локально) | 250 / 70 | 0–1 |
| 11 | Brand-repair hub: Bosch / LG / Samsung / Smeg / Miele (× city) | prestigerepairs | 150–400 | 0–12 |
| 12 | Fridge repair / regas cost (AU) | whybuy / melbournemetro | 70 | 0 |

---

*Дані Ahrefs станом на 2026-07. Трафік — оцінка. Обсяги/KD — Ahrefs Keywords Explorer, country=AU.*
