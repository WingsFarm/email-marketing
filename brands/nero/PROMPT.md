# NERO — Prompt → Email Spec

How to turn a short brief into finished NERO email HTML.

## Inputs you give me
```
type:     promo | drop | story | cart          (which template)
goal:     e.g. "20% off all bracelets, ends Friday"
logo:     <hosted URL>                          (set once, reuse)
hero:     <img URL> | "alt text"
products: name | price | product page URL | <img URL> | "alt"   (1–3 rows)
cta:      where the main button links
notes:    anything else (tone tweak, deadline, audience)
```
Anything missing → I ask or use a sensible brand default.

## What I produce
For each email, a folder: `emails/YYYY-MM-DD-slug/`
```
email.html   full HTML, ready to paste into Flashy custom-code block
meta.md      שורת הנושא (subject) + A/B variants + תיאור קצר לפתיחה (preheader)
```
- Hebrew copy (RTL) in NERO voice — see [brand-voice.md](brand-voice.md).
- Header (greige bar + logo) baked in. **No footer** — Flashy adds it.
- I also paste the HTML + subject + preheader in chat for quick grab.

### meta.md format
```markdown
# שורת הנושא
<primary subject> | פרסומת

## גרסאות נוספות
- <variant A> | פרסומת
- <variant B> | פרסומת

# תיאור קצר לפתיחה (preheader)
<preview text — also slotted into {{PREHEADER}} in the HTML>
```

### LEGAL — mandatory (Israeli anti-spam, תיקון 40)
- **Every** subject line + every A/B variant MUST end with ` | פרסומת`. No exceptions.
- Example: `50% הנחה לא יישארו לנצח 😎 | פרסומת`

## Templates
| type | structure |
|------|-----------|
| **promo** | header → hero → headline+CTA → product grid → trust badges |
| **drop**  | header → hero → story text → single product feature → CTA |
| **story** | header → hero → text block(s) → soft CTA |
| **cart**  | header → headline → the product → trust badges → CTA |
(only `promo` built so far; others on request)

## Copy rules (from brand voice)
- Quiet confidence. Short. Says less, means more.
- Lead with identity/meaning, not discount-shouting.
- Hebrew primary; English only as punchy accent.
- Reassure on durability + warranty, concretely.
- Headlines UPPERCASE, letter-spaced.
- **No em/en-dash** (— –) anywhere in copy or meta. Use a normal hyphen `-`, and use even that sparingly. Rephrase instead of dashing.

## Token reference (what gets filled)
`{{PREHEADER}}` inbox preview line ·
`{{LOGO_URL}}` ·
`{{HERO_IMG}}` `{{HERO_ALT}}` ·
`{{HEADLINE}}` `{{SUBCOPY}}` ·
`{{CTA_TEXT}}` `{{CTA_URL}}` ·
`{{P1..3_IMG/ALT/NAME/PRICE/URL}}`

## Image rules
- Public HTTPS URL, no auth, permanent.
- JPG/PNG (not WebP — Outlook desktop won't render).
- Always has `width` + `alt` (set in template already).

## Example brief
```
type: promo
goal: summer sale, 15% off all bracelets, code SUN15, ends Sunday
hero: https://cdn.you/summer-hero.jpg | "Man on beach wearing NERO bracelet"
products:
  צמיד אוניקס | ₪199 | https://nerostudio.co.il/p/onyx | https://cdn.you/onyx.jpg | "Onyx bracelet"
  צמיד חבל   | ₪179 | https://nerostudio.co.il/p/rope  | https://cdn.you/rope.jpg  | "Rope bracelet"
  סט קיץ     | ₪299 | https://nerostudio.co.il/p/set   | https://cdn.you/set.jpg   | "Summer set"
cta: https://nerostudio.co.il/collections/bracelets
```
→ I return finished promo.html with Hebrew copy + your URLs slotted in.

## Locked defaults
- Logo: `https://uploads.nadavezra.com/email/7a78de3c-b5b8-4933-8e54-e9268c58b75e.png` (baked into templates)

## To confirm
- Header bar color is my estimate `#D9D3C7` (greige). Confirm exact hex from brand.
