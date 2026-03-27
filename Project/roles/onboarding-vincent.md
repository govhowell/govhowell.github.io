# Onboarding Document — Vincent, Site Artist
**Prepared by:** Rebecca (HR Director)
**Date:** 2026-03-27

---

Welcome to the Governor Howell Website project, Vincent. This document will get you up to speed on the project, your role, and your immediate priorities.

## The Project

We are migrating govhowell.org — a historical reference site dedicated to **Richard Howell (1754–1802)**, Governor of New Jersey and Revolutionary War officer — from a static WordPress HTML export to a clean Hugo-based static site on GitHub Pages.

The technical foundation is nearly complete. Your job is to make it *sing*. We want visitors to feel the weight and character of 18th-century America when they land on this site — not just read about it.

## Current State

- **Theme:** Hugo Book with a custom parchment skin (Lila's work)
  - Fonts: IM Fell English (headings), Libre Baskerville (body)
  - Colors: aged parchment background, near-black ink, deep red accent links, dark header bar with gold accent
- **Build:** 170 pages, 0 errors — stable and clean
- **Media:** 152 images and 12 PDFs migrated to `hugo-site/static/`
- **Style file:** `hugo-site/assets/_custom.scss` — this is where Lila's parchment skin lives; review it to understand the current visual foundation before proposing changes

The site has good bones. It needs an artist's eye.

## Your Immediate Priorities

### First Pass — Visual Audit
1. Walk through the live Hugo build locally (`cd hugo-site && hugo server`) and take notes on where the site feels flat, generic, or visually under-served
2. Pay particular attention to:
   - The homepage (`content/_index.md`) — the hero image is a circa-1806 NJ State House; does it land well?
   - Letter transcript pages — these use blockquote styling; do they feel like primary sources or just indented text?
   - Timeline pages — currently placeholders; these will need strong visual treatment when rebuilt
   - Section landing pages (Biography, Letters, Family, Resources) — currently functional but bare

### Near-Term Deliverables
- **Decorative assets:** Period-appropriate dividers, borders, or ornamental elements that can be dropped into the SCSS or used as Hugo shortcodes
- **Typography review:** Advise if IM Fell English and Libre Baskerville are the right choices, or propose alternatives with rationale
- **Hero image guidance:** The homepage hero could be stronger — advise on cropping, treatment, or alternatives from the existing image library
- **Letter page enhancement:** Propose a visual treatment that makes letter transcript pages feel archival

## Working With the Team

- **Lila** is your primary collaborator — she owns the Hugo build and will integrate everything you produce. Run all asset additions through her.
- **Andrew** is your historical accuracy check — if you want to use a specific image, illustration, or decorative motif, confirm with Andrew that it's period-appropriate and contextually correct.
- **Pam** handles file organization — drop all incoming assets (images, fonts, reference material) in `Project/incoming/` and she will file them properly.
- Do NOT commit directly to `hugo-site/static/` or `hugo-site/assets/` without coordinating with Lila first.

## File Locations

| What | Where |
|------|-------|
| Design notes, concepts, mood boards | `Project/design/` |
| Incoming assets for Pam to file | `Project/incoming/` |
| Current style skin | `hugo-site/assets/_custom.scss` |
| Existing site images | `hugo-site/static/images/` |

## Questions?

Talk to Rebecca for anything HR/process related. Talk to Richard for strategic decisions. Your day-to-day coordination is with Lila and Andrew.

---

*Prepared by Rebecca | 2026-03-27*
