# Support Page — Design Spec
**Date:** 2026-05-05
**App:** Parlance — AI Speech Coach

---

## Overview

Add a `/support` page (`support.html`) to the parlance-site static site. Provides an accordion FAQ and a contact strip. Matches the design system established by `index.html` and `privacy.html`.

---

## Files Changed

| File | Change |
|------|--------|
| `support.html` | New file — FAQ accordion + contact strip |
| `privacy.html` | Update "parlance.app/support" link to `support.html` |

---

## Shell Structure

### Nav
- Fixed blurred nav, identical to `privacy.html`
- Left: `Parlance.` logo linking to `index.html`
- Right: `← Home` link

### Footer
- Same footer strip as `privacy.html` and `index.html`
- `© 2026 Parlance · Privacy Policy · Terms of Service`

---

## Page Sections

### 1. Page Header
- `padding-top: 8rem`, centered
- Heading: "Support" in Playfair Display 700
- Subtitle: "Get help with Parlance — AI Speech Coach" in `--sub`
- Thin bottom border separating from content

### 2. FAQ Accordion
- Max-width: 680px, centered
- Each item: question row + collapsible answer panel
- Question row: full-width button, question text on left, gold chevron icon on right
- Answer panel: smooth height animation (CSS max-height transition), `--sub` text, `0.95rem`
- Active state: chevron rotates 180°, answer visible
- Border between items: `1px solid var(--border)`
- First item open by default

**FAQ questions (in order):**
1. How does AI scoring work?
2. What's included in Pro?
3. Does Parlance work offline?
4. Why does the app need microphone access?
5. How do streaks work?
6. Is my audio stored anywhere?
7. How do I delete my data?
8. The app isn't responding — what should I do?

### 3. Contact Strip
- Card with `var(--card)` background, border, `var(--radius)` corners
- Heading: "Still need help?"
- Body: "Email us and we'll get back to you."
- Email link: `parlance.app@gmail.com` — styled gold, `mailto:` href
- Max-width: 480px, centered, `margin: 0 auto 5rem`

---

## Accordion Behavior

- Pure JS, no library
- Click toggles `active` class on the item
- Closing one item does NOT close others (multiple open allowed)
- Chevron: inline SVG, rotates 180° via CSS transform transition on `active`
- Height animation: `max-height: 0` → `max-height: 500px` with `overflow: hidden`
- First item open on page load

---

## Responsive
- Single column naturally — accordion is already full-width
- Contact card: full-width on mobile, max-480px on desktop
- Nav: same as other pages

---

## Animations
- Page header: `fade-up`
- FAQ section: `fade-up` on the container
- Contact strip: `fade-up`
- Same IntersectionObserver pattern as `privacy.html`

---

## Out of Scope
- Contact form (mailto link is sufficient for a static site)
- Search/filter on FAQ
- Categories/sections (8 questions doesn't warrant grouping)
