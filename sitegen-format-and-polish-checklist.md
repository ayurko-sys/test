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

## 3. Налаштування теми Sitegen (ЗАТВЕРДЖЕНО 2026-07-14, під реальні поля адмінки)

Sitegen дає 5 глобальних кольорів + 2 шрифти (Visual Identity) + окрему панель Form Appearance.
**Рішення:** `primary` = steel blue (НЕ амбер!), бо primary фарбує іконки/лінки/ховери по всьому сайту — амбер туди не можна за правилом DS. Амбер живе в Accent + Form Button, а CTA-кнопки блоків переводимо на accent адресно при допилі.

### Visual Identity
| Поле Sitegen | Значення | Токен DS |
|---|---|---|
| Primary Color | `#317CAB` | blue-500 (лого mark) — іконки, лінки, ховери |
| Secondary Color | `#1C507A` | blue-800 — utility top bar, click-to-call |
| Accent Color | `#E8730C` | amber-500 — строго CTA + Same-Day бейдж |
| Background | `#FFFFFF` | секції paper/mist — класами блоків при допилі |
| Text Color | `#141517` | ink |
| Heading Font | Archivo | Google Fonts |
| Body Font | Public Sans | Google Fonts |

Brand Tone: Professional (голос «expert neighbour» дотискаємо текстами).

### Form Appearance
| Поле | Значення | Токен DS |
|---|---|---|
| Form Background | `#FFFFFF` | |
| Text Color | `#141517` | ink |
| Border Color | `#D4DFE7` | line |
| Input Background | `#FFFFFF` | |
| Accent / Button | `#E8730C` | amber-500 |
| Button Hover | `#CC6410` | amber-600 |
| Placeholder Color | `#7D8B96` | slate-400 |
| Border Radius | `0.5rem` | = 8px radius-input/button (уже стоїть) |

### Ручні правки поверх теми (етап допилу блоків)
- CTA-кнопки блоків (`bg-primary`: header «Book Now», hero «Book Online Now», футерна band-кнопка) → амбер `#E8730C` з ink-текстом `#141517` (правило: один амберний CTA на в'юпорт).
- Сабміт форми: `text-white` → `#141517` (білий на амбері ~3:1 — фейл AA; ink = 6.1:1). Альтернатива, якщо потрібен білий текст: кнопка `#A94F0A` (5.5:1).
- Темні секції `bg-slate-900` → panel `#0E2B43` (blue-950).
- Зірки відгуків `text-yellow-400` → brand blue `#317CAB` (правило DS).
- Чергування фону секцій: paper `#F6F9FB` / mist `#EAF1F6`.
- Радіуси: кнопки/інпути 8px (`rounded-lg`), картки 16px (`rounded-2xl`) — прибрати мікс `rounded-full`/`rounded-xl`.
- muted-текст → slate-500 `#5B6A76`; борди → `#D4DFE7`; destructive `#C0392B`; focus ring `#317CAB` @35%.

### Відповіді платформи (зафіксовано)
- Дубль header/footer — лише артефакт редактора; на домені ок. Правимо САЙТ-ВАЙД версію (`SITE-WIDE HEADER`).
- Title/meta — поки не чіпаємо (нагадає власник).
- Форма: поля/структуру НЕ міняти, лише стиль. (Отже селекти «Appliance type»/«City» — скасовано.)
- JSON-LD schema — можна доставляти окремим блоком `<script type="application/ld+json">`.

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
- [ ] BLOCK 6 CONVERSION: поля НЕ чіпаємо (рішення платформи/власника) — тільки стиль: амберний сабміт з ink-текстом, борди `#D4DFE7`, радіус 8px; додати `id="booking"` секції для якорів «Book this»
- [ ] BLOCK 7 TESTIMONIAL: підписи «David S. — Surrey» ок; зірки → brand blue
- [ ] BLOCK 8: картки міст ок (районні списки вже локалізовані); «[Interactive Map Embed]» → реальний embed Google Map service area
- [ ] Footer: «North Delta · Ladner · Tsawwassen · South Surrey · Semiahmoo Peninsula» — чудово, лишити

### Далі (наступні сторінки)
- Локації: структура за затвердженим планом (промо → сервіси+місто → райони → бренд+місто блоки → відгуки міста → FAQ → форма)
- Бренди: промо → типи техніки з brand-specific болями → service area → recent jobs (проблема→фікс→район) → форма, БЕЗ відгуків
- About Us: тільки текст, без картинок/цифр

---

## 5. Питання до платформи — ВСІ ЗАКРИТІ (відповіді в кінці розділу 3)

1. ~~Тема~~ → Visual Identity + Form Appearance в адмінці (значення затверджено в розділі 3).
2. ~~Дубль header/footer~~ → артефакт редактора, на домені ок.
3. ~~Title/meta~~ → відкладено, нагадає власник.
4. ~~Кастомні поля форми~~ → форму не міняємо, тільки стиль.
5. ~~JSON-LD~~ → так, окремим script-блоком.
