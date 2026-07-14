# Sitegen — формат коду та чекліст допилу (Claude Code)

**Джерело:** код сторінки Home від Sitegen, 2026-07-14. Стек: статичний HTML + Tailwind CSS (CDN `cdn.tailwindcss.com`).

---

## 1. Конвенції формату (як працює генератор)

| Елемент | Конвенція |
|---|---|
| Блоки | `<!-- BLOCK N: TYPE (ID: uuid) -->` — типи: NAVIGATION, HERO, FEATURE, TRUST, CONVERSION, TESTIMONIAL. Редагуємо адресно по ID блоку |
| Site-wide частини | `<!-- STYLING-HEADER -->` / `<!-- STYLING-FOOTER -->` — правки застосовуються глобально до всього проєкту |
| NAP-змінні | `{{nap.business_name}}`, `{{nap.phone}}`, `{{nap.phone_tel}}`, `{{nap.address}}` — підставляються платформою |
| Редаговані тексти | `data-editable="..."` (headline, subheadline, body, title, description, cta, text) |
| Редаговані зображення | `data-image-editable="true"`, зображення на Supabase storage |
| Кольори | shadcn-стиль семантичні токени: `bg-primary`, `text-primary-foreground`, `bg-secondary`, `text-foreground`, `text-muted-foreground`, `bg-card`, `border-border`, `text-destructive`, `bg-background` — тема інжектиться платформою (tailwind.config) |
| Форма | `data-contact-form` + власний JS: маска телефону +1, валідація, POST на `__FORM_ENDPOINT__`, CallRail capture (`CallTrk.captureForm`), `dataLayer.push({event:'generate_lead'})`, IP через ipify |
| Іконки | інлайн SVG (heroicons-стиль, stroke 2px) |

---

## 2. Баги генерації (виправити першими)

1. **Дубльований header і footer у DOM** — `STYLING-HEADER` + `BLOCK 1: NAVIGATION` ідентичні; те саме `BLOCK 9` + `STYLING-FOOTER`. Дубльований `id="mobile-menu"` → hamburger керує лише першим меню; невалідний HTML. З'ясувати: це артефакт прев'ю чи потрапляє в експорт. Якщо експортується — видаляти дубль-блоки на кожній сторінці.
2. **Хардкод телефону в Hero:** `tel:+15555555555` і `(555) 555-5555` замість `{{nap.phone_tel}}` / `{{nap.phone}}` (у 2 місцях: hero CTA і картка «Not sure?»).
3. **Контраст-баги (текст майже невидимий):** `text-slate-200` на білому — дати відгуків (`text-xs text-slate-200`), описи міст у картках локацій (BLOCK 8), плейсхолдер мапи. Мають бути `text-slate-500`/`text-slate-600`.
4. **`data-editable="body"` на `<path>` SVG-елементах** — сміттєві атрибути редактора всередині іконок (hero, services). Вичистити при фінальному експорті.
5. **Інлайн-стиль замість токена:** footer CTA `style="background-color: hsl(217, 91%, 60%)"` — замінити на клас з теми (accent).
6. **Hover-only дропдауни** (Locations/Brands) — недоступні з клавіатури; додати `focus-within` або JS-toggle. Мобільне меню: хардкод `top-[96px]`.

---

## 3. Мапінг дизайн-системи Fraser → Tailwind-тема Sitegen

З Claude design проєкту `Fraser Appliance Repair Design System` (`tokens/colors.css`):

| Tailwind токен | Значення Fraser DS | Примітка |
|---|---|---|
| `primary` | **amber `#E8730C`** | CTA-кнопки «Book Now» (в коді вони `bg-primary`) — амбер строго тільки CTA + Same-Day бейдж |
| `primary-foreground` | ink `#141517` | по DS на амбері — темний текст (6.1:1), НЕ білий |
| `secondary` | deep blue `#1C507A` | utility top bar (`bg-secondary`), click-to-call кнопки |
| `foreground` | ink `#141517` | |
| `muted-foreground` | slate-500 `#5B6A76` | |
| `background` / `card` | `#FFFFFF`, alt `#F6F9FB` (paper) / `#EAF1F6` (mist) | секції, що чергуються |
| `border` | line `#D4DFE7` | |
| темні секції | `bg-slate-900` → panel **`#0E2B43`** (blue-950) | hero-оверлей, TRUST-стрічка, футер |
| `destructive` | `#C0392B` | |
| focus ring | steel blue `#317CAB` @35% | |
| Зірки відгуків | **brand blue `#317CAB`**, не `text-yellow-400` | правило DS |
| Радіуси | кнопки/інпути 8px (`rounded-lg`), картки 16px (`rounded-2xl`) | у коді мікс `rounded-full`/`rounded-lg`/`rounded-xl` — уніфікувати |
| Шрифти | Archivo (заголовки) + Public Sans (текст), Google Fonts | додати `<link>` + font-family у тему |

---

## 4. SEO-допил по сторінках (чекліст для Claude Code)

### Глобально
- [ ] `<title>` + `<meta name="description">` на кожну сторінку (з'ясувати, де це в Sitegen — head зараз «Page Preview»)
- [ ] Canonical, OG-теги
- [ ] JSON-LD: `HomeAndConstructionBusiness` на Home (name, phone, areaServed: Surrey/Delta/White Rock, openingHours, sameAs); `Service` + `areaServed` на сторінках локацій; `FAQPage` де є FAQ
- [ ] Alt-тексти зображень: конкретика замість «Modern kitchen appliances» (без людей/техніків — правило)
- [ ] Canadian spelling всюди (labour, neighbourhood, centre)
- [ ] Один H1 на сторінку; перевірити ієрархію H2/H3

### Home (по блоках з коду)
- [ ] BLOCK 2 HERO: телефон з NAP-змінних; бейдж гарантії — фінальний термін (зараз «90-Day», рішення: 90 днів чи 6 міс — узгодити)
- [ ] BLOCK 3: інтро-текст ок (Fraser River storytelling) — лишити
- [ ] BLOCK 4 Services: 5 карток + «Not sure?» — додати Freezer (окремо чи в Refrigerator) і Range hood за потреби; посилання «Book this» → на `#booking`-якір форми (якір існує? зараз форма без `id="booking"` — додати)
- [ ] BLOCK 5 TRUST: бренд-стрічка ок (5 брендів лінками + другорядні текстом) — другорядні бренди (GE, Maytag…) зробити теж клікабельними колись з'являться сторінки; поки лишити
- [ ] BLOCK 6 CONVERSION: додати поля «Appliance type» (select) і «City» (select: Surrey/Delta/White Rock) — ОНОВИТИ і payload у JS (зараз hardcoded name/phone/email/terms)
- [ ] BLOCK 7 TESTIMONIAL: підписи «David S. — Surrey» ок; зірки → brand blue
- [ ] BLOCK 8: картки міст ок (районні списки вже локалізовані); «[Interactive Map Embed]» → реальний embed Google Map service area
- [ ] Footer: «North Delta · Ladner · Tsawwassen · South Surrey · Semiahmoo Peninsula» — чудово, лишити

### Далі (наступні сторінки)
- Локації: структура за затвердженим планом (промо → сервіси+місто → райони → бренд+місто блоки → відгуки міста → FAQ → форма)
- Бренди: промо → типи техніки з brand-specific болями → service area → recent jobs (проблема→фікс→район) → форма, БЕЗ відгуків
- About Us: тільки текст, без картинок/цифр

---

## 5. Питання до платформи Sitegen (з'ясувати в адмінці)

1. Де редагується tailwind-тема (мапінг `primary`/`secondary`/...)? Потрібно вшити палітру Fraser DS (розділ 3).
2. Дубль header/footer — прев'ю-артефакт чи потрапляє в продакшн-експорт?
3. Де задаються `<title>`/`<meta description>` per page?
4. Чи можна додати кастомні поля у форму зі збереженням інтеграції (`__FORM_ENDPOINT__` приймає довільний JSON?), і чи CallRail captureForm підхопить нові поля?
5. Чи можна вставити довільний `<script type="application/ld+json">` блок (для schema)?
