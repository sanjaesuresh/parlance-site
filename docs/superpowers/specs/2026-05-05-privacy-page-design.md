# Privacy Policy Page — Design Spec
**Date:** 2026-05-05
**App:** Parlance — AI Speech Coach

---

## Overview

Add a `/privacy` page (`privacy.html`) to the parlance-site static site that presents the app's full privacy policy. Update `index.html` to add a footer strip with a link to this page.

---

## Files Changed

| File | Change |
|------|--------|
| `privacy.html` | New file — the full privacy policy page |
| `index.html` | Add `<footer>` strip after `#cta` section |

---

## Page Metadata

- **Title:** `Privacy Policy — Parlance`
- **Description:** `How Parlance handles your voice data, AI processing, and session history`
- **Effective date:** May 5, 2026 (hardcoded — no build tooling)
- **Support email:** parlance.app@gmail.com

---

## Shell Structure

### Nav
- Identical fixed nav from `index.html`: blurred cream background, `Parlance.` logo on the left
- Right side: replace "Coming Soon" CTA with a plain `← Home` link (styled like `.nav-cta` but lower-key — outline or muted variant) pointing to `index.html`

### Footer Strip
Added to **both** `privacy.html` and `index.html` (after `#cta`).

```
© 2026 Parlance  ·  Privacy Policy  ·  Terms of Service
```

- Small text (`0.8rem`), `--sub` color
- Centered, `2rem` vertical padding
- "Privacy Policy" links to `privacy.html`
- "Terms of Service" is a non-linked span (or placeholder `#`) until that page exists
- Background: `var(--bg)` (same as page background — sits below the dark CTA rounding)

---

## Privacy Page Layout

### Page header section
- `padding-top: 7rem` (clears the fixed nav)
- `text-align: center`
- Display heading: `Privacy Policy` using `.display` (Playfair Display 700)
- Below heading: two lines of subdued metadata
  - `Effective date: May 5, 2026`
  - `Questions? parlance.app@gmail.com`
  - Both in `--sub` color, `0.9rem`
- Thin horizontal rule or bottom border separating header from content

### Content area
- `max-width: 720px`, centered via `margin: 0 auto`
- `padding: 3rem 1.5rem 5rem`
- `text-align: left` — prose, not centered like marketing sections

### Section headings (h2)
- `font-size: 1.1rem`, `font-weight: 700`, `color: var(--text)`
- `border-left: 3px solid var(--gold)`, `padding-left: 0.75rem`
- `margin: 2.5rem 0 0.75rem`

### Body text
- `font-size: 0.95rem`, `line-height: 1.75`, `color: var(--sub)`
- Bold terms (`<strong>`) use `color: var(--text)`
- Unordered lists: no list-style bullets — use a `·` or thin dash via `::before`, indent with `padding-left: 1rem`

---

## Third-Party Services — Card Layout

Instead of a raw `<table>` (no table styles exist), render three service cards in a row.

Each card:
- Background: `var(--card)`, border: `1px solid var(--border)`, `border-radius: var(--radius)`
- Padding: `1.25rem`
- Service name as `<strong>` (`--text`)
- Purpose line in `--sub`
- Privacy policy link: small, gold color, links to external privacy URL

Layout:
- Desktop: `display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem`
- Mobile (< 600px): single column

Services:
1. **Anthropic (Claude)** — AI coaching feedback — `anthropic.com/privacy`
2. **Hume AI** — Vocal emotion analysis (Pro) — `hume.ai/privacy`
3. **Cloudflare Workers** — Secure API proxy — `cloudflare.com/privacypolicy`

---

## Content Sections (in order)

1. What We Collect
   - Sub-groups: "On your device", "Transmitted to our servers", "Transmitted for Pro subscribers only" — each as a bold label followed by a bullet list
2. How We Use It
3. AI Processing
4. Data Storage & Security
5. Your Rights
6. Third-Party Services (card layout)
7. Children
8. Changes
9. Contact

---

## Animations

- `fade-up` class on the page header and content sections — reuse the same IntersectionObserver script from `index.html`
- No tab switching, no metric bars — just the scroll-reveal fade

---

## Responsive

- Nav: same breakpoints as `index.html`
- Content: single column, naturally responsive via `max-width` + padding
- Service cards: 3-col → 1-col at 600px
- Footer strip: always centered, wraps naturally

---

## Out of Scope

- Terms of Service page — footer link is a placeholder
- Any server-side rendering or build tooling
- New navigation items in the top nav (privacy page is footer-linked only)
