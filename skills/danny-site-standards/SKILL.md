---
name: "danny-site-standards"
description: "Apply Danny's reusable design, content, and delivery standards when building or updating his bilingual (ES/EN) landing pages and micro-SaaS tool sites — so he never has to re-explain his preferences."
---

# Danny Site Standards

## Purpose
One coherent checklist for every Danny site: bilingual single-file HTML, responsive, GA4, brand contacts, affiliate/AdSense conventions, design bar, and exact delivery rules. Trigger whenever building a new site or updating an existing one for Danny.

## Workflow
1. Identify the brand → contact email + domain (see Contacts).
2. Build/update as a single `index.html`: bilingual ES/EN via `data-i18n` dictionary, ES/EN toggle in header, language persisted in `localStorage`, `<html lang>` updated on switch, localized canonical + meta.
3. Include GA4 `G-5VGT1LL1V7`; responsive layout (media queries, `clamp()` fluid type).
4. Apply the design bar: propose a quality benchmark up front, state negative constraints, grade the output against the benchmark, iterate on Danny's feedback.
5. Add subtle reveal-on-scroll + card hover lift; always respect `prefers-reduced-motion`.
6. Tool sites: Nosotros/About + Privacidad/Privacy as super-small fine print, affiliates/AdSense per conventions below.
7. Deliver per Delivery Rules; reply in Spanish (steps for apps/phones/websites in ENGLISH).

## Standards

### 1. Bilingual ES/EN
- Single `index.html`, `data-i18n` dictionary (80–100 keys typical), applied via `data-i18n` attributes.
- ES/EN toggle buttons in the header; persist choice in `localStorage` (`site-locale`); update `<html lang>` on every switch.
- Localized `<title>`, meta description, and canonical. Example skeleton in `references/snippets.md`.

### 2. Responsive
- Must look right on phones, tablets, and desktop. Breakpoint around 900px; fluid type with `clamp()`; no horizontal scroll at 360px.

### 3. Analytics
- GA4 property `G-5VGT1LL1V7` snippet in `<head>` of every site. Snippet in `references/snippets.md`.

### 4. Delivery rules
- Existing site update → deliver ONLY `index.html` (+ `img/` folder only if images changed). Never rebuild a ZIP for an index-only update.
- Brand-new site → deliver a ZIP containing `index.html` + `img/`.
- Every delivery states: exact domain, folder (usually `public_html` root), which files overwrite what, and a hard-refresh reminder (`Ctrl/Cmd + Shift + R`).

### 5. Design quality bar (Anthropic Academy: "create a custom webpage")
- Name a benchmark up front: "premium SaaS like Stripe/Linear" or "top-tier consulting report".
- State negative constraints explicitly: "no generic corporate blue", "no default typography", "no lorem ipsum".
- Grade your own output against the benchmark before delivering; refine; iterate on Danny's surgical feedback without debate.

### 6. Motion
- Reveal on scroll: `IntersectionObserver`, `translateY(26px)` → 0, `0.7s ease`; gentle card hover lift (`translateY(-4px)`).
- Always disable under `@media (prefers-reduced-motion: reduce)`. Snippets in `references/snippets.md`.

### 7. Typography
- Barlow family. Tool sites: Nosotros/About + Privacidad/Privacy as super-small fine print (`.72rem` paragraphs, `17px` headings), footer `.72rem`.

### 8. Contacts per brand
- FOMSYS → `info@fomsys.com`
- LearnAndBuildIt network → `info@learnandbuildit.com`
- TipsPet → `contact@tipspet.com`
- PortalBebé → `contact@portalbebe.com`
- Use in footer + CTA `mailto:` links.

### 9. Affiliates
- Amazon tags: TipsPet `tipspet-20`, PortalBebé `portalbebe-20`, TipsBici `tipsbici-20`, YourTipsPlan `fitplan05-20`.
- Danny provides short `amzn.to` links; apply the site's tag before placing.
- `data-aff` attributes on affiliate anchors (e.g. `data-aff="tb-amz-11"`); `COUNTRY_LINKS` structure for US/CA/CL/CR (US live, others may fall back to US). Skeleton in `references/snippets.md`.

### 10. AdSense
- Publisher `ca-pub-7766400563732002`. Ad slots render as `data-ad-slot="PENDIENTE"` until Danny provides real slot IDs or enables Auto Ads.

### 11. Communication
- Reply to Danny in Spanish, direct, with concrete numbers.
- Any step-by-step instructions for apps, phones, or websites go in ENGLISH (his devices are in English).

## Output Contract
Every build/update delivers: the file(s) per Delivery Rules, the exact upload target (domain + folder + overwrite list), a hard-refresh reminder, and confirmation that brand contact, GA4, and i18n checks passed.

## Operating Rules
1. Danny enters cards and credentials himself — never ask for or store them.
2. Never attribute a caching issue to Cloudflare (he has never used it); first verify what the server is actually serving.
3. Don't re-litigate closed decisions (abandoned domains, paused features, his own reminders).
