# Onboarding Document — Lila, Chief Web Designer & Architect
**Prepared by:** Rebecca (HR Director)
**Date:** 2026-03-26

---

Welcome to the Governor Howell Website project, Lila. This document will get you up to speed on the project, your role, and your immediate priorities.

## The Project

We are migrating govhowell.org — currently a static WordPress HTML export — into a clean **Hugo-based static site** deployable on **GitHub Pages**. The site is a historical reference dedicated to Richard Howell (1754–1802), Governor of New Jersey and Revolutionary War officer.

You own the technical and design vision of the new site. This is your build.

## Current State (What You're Inheriting)

```
govhowell.org/
├── index.html                        ← Homepage (WordPress export)
├── [content sections]/index.html     ← 28 additional pages
├── wp-content/uploads/               ← 806 media files (images, PDFs, docs)
├── wp-content/themes/                ← Old WP theme (not reusable)
├── wp-includes/                      ← WordPress core (discard)
└── new-web-page-design/              ← A previous redesign attempt (review this!)
```

**Key observation:** There are zero markdown files. All content must be extracted from HTML and converted.

## Your Immediate Priorities

### Week 1
1. **Structural Audit** — Review all 29 HTML files and map the site's information architecture. Document in `Project/site-audit/structure-audit.md`
2. **Theme Research** — Identify 3 Hugo theme candidates appropriate for a historical/scholarly site. Document with screenshots/links in `Project/design/theme-options.md`
3. **Review `new-web-page-design/`** — Assess if anything from the previous redesign attempt is worth salvaging

### Week 2
- Present theme options to Richard for decision
- Set up Hugo project scaffold in a new directory (do NOT modify the existing HTML files)
- Define content types and taxonomy (pages, letters, timeline entries, people, events)
- Draft URL structure plan

### Ongoing
- Convert HTML content to Hugo-compatible markdown (coordinate with Andrew for accuracy)
- Set up GitHub Actions for GitHub Pages deployment
- Create contributor style guide

## Technical Notes

- **Hugo recommended** — Richard's preference. Make the case for an alternative if you find something better.
- The site is content-heavy with multiple taxonomy types (timelines, letters, biographies, events) — choose a theme that handles this well
- Historical/archival aesthetic is appropriate — think clean, readable, maybe a serif-friendly theme
- Mobile-responsive is required
- No JavaScript frameworks — keep it simple and fast

## Working Norms

- File design specs, mockups, and notes in `Project/design/`
- File your site audit work in `Project/site-audit/`
- Drop incoming assets (fonts, images, references) in `Project/incoming/` — Pam will organize them
- Coordinate with Andrew before finalizing content structure — he may have research that affects how content should be organized
- Escalate technology decisions above theme selection to Richard via Rebecca

## Questions?

Talk to Rebecca for anything HR/process related. Talk to Richard for strategic decisions. Coordinate directly with Andrew on content and historical accuracy questions.

---

*Prepared by Rebecca | 2026-03-26*
