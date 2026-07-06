# Sitegen "Visual Identity" settings (editor screenshot)

Transcribed from the editor's internal **Visual Identity — "Colors and fonts for
your website"** panel. Panel note (verbatim): *"These colors and fonts are used
by the AI when generating content and by the deployment template."* → these five
colors + two fonts are authoritative for the deployed site and drive the semantic
Tailwind tokens (`primary`, `secondary`, `accent`, `background`, `foreground`).

## Colors (the only five the editor exposes)

| Editor field | Hex | Maps to Tailwind token | CLAUDE.md token | Match? |
|---|---|---|---|---|
| Primary Color | `#2E5636` | `primary` (`bg-primary`, `text-primary`) | `--forest` | ✅ |
| Secondary Color | `#1F3D26` | `secondary` | `--forest-deep` | ✅ |
| Accent Color | `#C29A55` | `accent` (`border-accent`) | `--gold` | ✅ |
| Background | `#F7F3EA` | `background` (`bg-background`) | `--cream` | ✅ |
| Text Color | `#26261F` | `foreground` (`text-foreground`) | `--ink` | ✅ |

All five match CLAUDE.md exactly. The editor does **not** expose the remaining
CLAUDE.md tokens — `--gold-deep #8A6A2F`, `--bark #5F482A`, `--paper #FFFFFF`,
`--sage #E7EFE7`, `--border #E4DCC9`. Those must be written as arbitrary Tailwind
hex classes (`bg-[#E4DCC9]`) or inline `style` per block (the sample does this).

## Fonts

| Editor field | Value | CLAUDE.md wants | Match? |
|---|---|---|---|
| Heading Font | **Lora** | Fraunces | ❌ CONFLICT |
| Body Font | **Nunito Sans** | Figtree | ❌ CONFLICT |

Preview strings shown for both: "The quick brown fox jumps over the lazy dog — 1234567890".

⚠ The live editor is configured with **Lora + Nunito Sans**, not the
CLAUDE.md **Fraunces + Figtree**. Because the panel says these fonts feed the
deployment template, the deployed site will use Lora/Nunito Sans unless the
client changes them here. Needs a decision — see SITEGEN-NOTES.md §5.
