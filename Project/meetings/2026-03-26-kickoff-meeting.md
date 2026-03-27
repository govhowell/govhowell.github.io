# Kickoff Meeting — Governor Howell Website Project
**Date:** 2026-03-26
**Recorded by:** Pam (Admin)
**Chaired by:** Richard (Project Manager)

---

## Attendees
| Name | Role |
|------|------|
| Richard | Project Manager |
| Rebecca | HR Director |
| Andrew | Chief Researcher & Historian |
| Lila | Chief Web Designer & Architect |
| Pam | Project Admin (newly hired) |

---

## Agenda

1. Project Overview & Goals
2. Role Assignments
3. Current Site Assessment
4. Technology Decision
5. Next Steps & Action Items

---

## 1. Project Overview & Goals

**Richard opened the meeting:**

The Governor Howell Website (govhowell.org) is a historical reference site dedicated to Richard Howell, Governor of New Jersey and Revolutionary War figure. The current site is a WordPress export — a static dump of HTML files with no CMS behind it. It is disorganized, difficult to maintain, and not suitable for long-term preservation or easy publishing.

**Stated goal:** Migrate the site content to a modern markdown-based static site generator, suitable for hosting on GitHub Pages or similar. The preferred platform is **Hugo**, though the team is empowered to recommend the best tool for the job if a stronger case can be made.

**Success criteria:**
- Clean, readable markdown content files
- Historical accuracy preserved and improved
- Site deployable via GitHub Pages with a single command
- Easy for non-technical contributors to add/edit content
- Attractive, historically appropriate design

---

## 2. Role Assignments

*(Rebecca presented the role definitions she prepared — see `roles/role-definitions.md` for full detail)*

| Name | Role | Primary Responsibilities |
|------|------|--------------------------|
| Richard | Project Manager | Oversight, guidance, final decisions, no hands-on work |
| Rebecca | HR Director | Role definitions, talent acquisition, team coordination |
| Andrew | Chief Researcher & Historian | Content accuracy, historical research, source verification |
| Lila | Chief Web Designer & Architect | Site structure, Hugo/SSG setup, theme, UX |
| Pam | Project Admin | Meeting minutes, change log, file management, incoming files |

---

## 3. Current Site Assessment (Preliminary)

A quick audit of the existing site files was conducted prior to this meeting:

- **29 HTML files** across the site — all static WordPress exports
- **0 Markdown files** — all content must be extracted and converted
- **806 media files** in `wp-content/uploads/` — images, documents, PDFs to be inventoried
- **Key content sections identified:**
  - Timelines (Revolutionary War, Pre-War, Post-War)
  - Letters (Pre-War, Post-War, individual correspondence)
  - Biographical pages (Dr. Lewis Howell, Varina Howell Davis, William Howell, etc.)
  - Historical events (Greenwich Tea Burning, 2nd NJ Regiment, etc.)
  - Family tree, maps, documents
  - Blog section

Andrew will lead a full content audit. Lila will lead a structural/design audit. See `site-audit/` folder for working documents.

---

## 4. Technology Decision

**Lila's preliminary recommendation:** Hugo (confirmed as first choice)

**Rationale:**
- Fastest static site generator available
- Excellent support for content-heavy, multi-section sites
- Strong GitHub Pages integration
- Large library of historical/document-style themes
- Markdown + front matter maps cleanly to the existing content structure

**Decision:** Proceed with Hugo as the platform. Lila to finalize theme selection and present options within one week.

---

## 5. Action Items

| # | Action | Owner | Due |
|---|--------|-------|-----|
| 1 | Finalize role definitions document | Rebecca | 2026-03-28 |
| 2 | Conduct full HTML content audit — map all pages | Lila + Andrew | 2026-04-02 |
| 3 | Inventory and categorize all media in wp-content/uploads | Pam | 2026-04-02 |
| 4 | Research and select Hugo theme candidates (3 options) | Lila | 2026-04-02 |
| 5 | Begin historical fact-check of existing content | Andrew | Ongoing |
| 6 | Set up Project folder structure and change log | Pam | 2026-03-26 ✓ |
| 7 | Schedule next team meeting | Pam | 2026-03-28 |

---

## Richard's Closing Notes

> "This is a preservation project as much as a technology project. Governor Howell's legacy deserves a clean, professional, and historically accurate home on the web. Let's make sure we're not just migrating junk — we're building something that will last. Andrew, I'm counting on you to keep us honest on the history. Lila, I want a site that looks the part. Rebecca, keep the team organized. Pam, document everything."

---

*Minutes recorded by Pam | Next meeting TBD*
