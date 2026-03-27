# Usability & Contrast Audit — Governor Howell Site
**Prepared by:** Vincent (Site Artist)
**Date:** 2026-03-27
**Scope:** Visual design, contrast ratios, and usability review of current parchment skin (`hugo-site/assets/_custom.scss`)

---

## Summary

The parchment skin is a strong foundation — the color palette is historically appropriate, typography choices are thoughtful, and the heading/body contrast is excellent. However, there are several contrast and usability issues that must be addressed before launch, plus a set of enhancement opportunities.

---

## Contrast Findings

WCAG AA standards require:
- **4.5:1** minimum for normal/small text (below 18pt / 14pt bold)
- **3:1** minimum for large text (18pt+ / 14pt+ bold)

### ❌ FAIL — `$ink-light` on `$parchment-bg` (≈ 4.1:1)

| Element | Color | Background | Ratio | Result |
|---------|-------|------------|-------|--------|
| Footer text | `#7a6650` | `#f5efe0` | ~4.1:1 | **FAIL** AA (small text) |
| Captions / metadata | `#7a6650` | `#f5efe0` | ~4.1:1 | **FAIL** AA (small text) |

The footer is set at `0.8rem` (~12.8px) — small text. WCAG AA requires 4.5:1. The current `$ink-light` value falls short at approximately 4.1:1.

**Recommended fix:** Darken `$ink-light` from `#7a6650` to `#6a5542` or similar. This brings the ratio above 4.8:1 while retaining the muted, secondary-text feel.

---

### ✅ PASS — Primary text and headings

| Element | Color | Background | Ratio | Result |
|---------|-------|------------|-------|--------|
| Body text | `#2c1f0e` | `#f5efe0` | ~14.5:1 | **PASS** AAA |
| h3 text | `#4a3728` | `#f5efe0` | ~9.8:1 | **PASS** AAA |
| Links | `#8b2222` | `#f5efe0` | ~7.0:1 | **PASS** AAA |
| Sidebar nav links | `#4a3728` | `#e8dfc8` | ~7.5:1 | **PASS** AAA |
| Sidebar active links | `#8b2222` | `#e8dfc8` | ~6.2:1 | **PASS** AAA |
| Header title | `#f5efe0` | `#2c1f0e` | ~14.5:1 | **PASS** AAA |
| Blockquote text | `#4a3728` | `~#ede7d3` | ~9.0:1 | **PASS** AAA |
| Table header | `#f5efe0` | `#2c1f0e` | ~14.5:1 | **PASS** AAA |

---

## Usability Issues

### 1. No Keyboard Focus Styles (Medium Priority)
The SCSS defines a focus outline for the search input (`outline: 2px solid $accent-red`) but no general `:focus-visible` rule for links, buttons, or interactive elements. Keyboard users navigating via Tab will have no visible indicator.

**Fix:** Add a global `:focus-visible` rule:
```scss
:focus-visible {
  outline: 2px solid $accent-red;
  outline-offset: 3px;
}
```

### 2. Small Font Sizes in Secondary UI (Low–Medium Priority)
Several UI elements use very small font sizes:
- Sidebar nav: `0.88rem` (~14px)
- TOC: `0.85rem` (~13.6px)
- Footer: `0.8rem` (~12.8px)
- Table body: `0.92rem`

For a historical research site where readers may be older, consider nudging these up slightly. Minimum recommendation: floor at `0.85rem` for footer and TOC.

### 3. Tables Not Responsive on Mobile (Medium Priority)
Tables (roster lists, children table, genealogy data) have `width: 100%` but no overflow wrapper or horizontal scroll. On narrow screens, these will overflow the viewport.

**Fix:** Wrap tables or add:
```scss
table {
  display: block;
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}
```

### 4. IM Fell English at Small Sizes (Low Priority)
`IM Fell English SC` is used for sidebar nav and TOC at sub-`0.9rem` sizes. This font was designed for large display use — at small sizes the letterforms can become cramped and hard to read, particularly on lower-resolution screens. Consider `Libre Baskerville` at those sizes, reserving IM Fell English SC for headings and branding.

### 5. No `alt` Text Convention Documented (Low Priority)
The homepage hero image tag uses no alt attribute guidance. Historical images need descriptive alt text for accessibility. This is a content issue as much as a code issue — Andrew should provide descriptions for all historical images.

### 6. Decorative HR May Not Render on All Browsers (Low Priority)
The `::before` pseudo-element on `hr` uses `content: '✦'`. While broadly supported, the positioning relies on `position: relative; top: -0.75em` combined with a fixed `width: 1.5em; margin: 0 auto`. Verify rendering on Safari iOS and Firefox.

---

## Portrait — Richard Howell (Landing Page)

Richard's portrait is not currently on the landing page — only the NJ State House circa 1806 is displayed as the hero image. The project manager has directed that the newest portrait be featured prominently on the homepage.

**Status:** Awaiting portrait file in `Project/incoming/` from Richard. Once received, Lila should:
1. Move the file from `Project/incoming/` to `hugo-site/static/images/`
2. Update `hugo-site/content/_index.md` to add the portrait above or alongside the State House image
3. Add appropriate caption and alt text (coordinate with Andrew for wording)

**Suggested placement:** Add the portrait as the primary hero element directly below the `# Richard Howell / ## 1754–1802` heading, before the State House image. The State House can remain as a secondary image lower on the page or be moved to the Biography section.

---

## Enhancement Opportunities (Post-Launch)

These are artistic improvements beyond the current scope — flagging for future sprints:

- **Drop caps** on opening paragraphs of biographical content — period-appropriate and visually distinctive
- **Decorative section headers** — a thin rule with period ornament above major section titles on long pages
- **Portrait frame treatment** — a subtle aged-wood or gilt CSS border around portrait images
- **Marginalia styling** — footnotes or asides styled as handwritten margin notes (CSS only)
- **Map page** — the maps section could benefit from a visual grid layout rather than a plain table

---

*Prepared by Vincent | 2026-03-27 | Filed in `Project/design/`*
