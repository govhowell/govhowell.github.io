# Project Change Log — Governor Howell Website
**Maintained by:** Pam (Project Admin)

> This log records all significant decisions, changes, and milestones. Entries are added in reverse chronological order (newest first).

---

## 2026-03-27 — SITE LIVE at govhowell.org ✅

### Deployment Complete
- GitHub repository created: `github.com/govhowell/govhowell.github.io`
- SSH key generated (`id_govhowell`) and added to GitHub for authentication
- Hugo site pushed to `master` branch — single clean orphan commit
- GitHub Actions workflow (`deploy.yml`) builds Hugo on push to `master`, publishes built output to `gh-pages` branch
- GitHub Pages configured: source = `gh-pages / (root)`, custom domain = `govhowell.org`
- `.nojekyll` added to repo root to prevent GitHub's Jekyll builder from interfering
- **govhowell.org confirmed live and loading correctly**

### Repository Restructure
- WordPress HTML export files deleted from repo (all untracked debris removed)
- `hugo-site/` subdirectory eliminated — Hugo source moved to repo root
- `hugo-site/.git` (empty nested repo) and broken submodule `.git` file removed
- hugo-book theme vendored directly as regular files (pinned commit `751bde0`)
- `deploy.yml` updated: removed `submodules: recursive`, removed `working-directory: hugo-site`, changed `publish_dir` to `./public`, trigger changed from `main` → `master`
- `start_webserver.sh` updated: `HUGO_DIR` now points to repo root
- `.gitignore` updated: removed `hugo-site/` prefixes, added `.DS_Store`, `.vscode/`, `*.swp`
- Repository history squashed to single clean commit via orphan branch

### Outstanding Items
- GitHub Actions Node.js 20 deprecation warning — update action versions before June 2, 2026
- Formspree contact form — requires Lila to configure endpoint for govhowell.org domain
- Lewis Howell death date — three conflicting sources; primary source verification pending
- Clarence Parvin — name needs verification against *Tea Burners of Cumberland County*
- Action SHA pinning — `peaceiris/actions-hugo@v3` and `peaceiris/actions-gh-pages@v4` should be pinned to commit SHAs

---

## 2026-03-27 (updated — Richard Howell portrait added to homepage)

### Portrait Placed on Homepage
- Portrait file received in `Project/incoming/`: `01-Richart_Howell_age45_no_frame.png`
- Filename typo corrected ("Richart" → "Richard"); filed to `hugo-site/static/images/richard-howell-portrait.png` (Terry)
- Homepage (`content/_index.md`) updated: portrait now appears as primary hero directly below name/title heading
- New Jersey State House image relocated to below the introductory text as a secondary illustration
- Portrait frame CSS added to `_custom.scss`: double-rule border (parchment + gold outline), period drop-shadow, centered layout with italic IM Fell English caption (Vincent)
- **Build:** 170 pages, 235 static files, 0 errors ✅
- **Actioned by:** Vincent (design direction), Terry (file migration), Lila (implementation)

---

## 2026-03-27 (updated — full implementation sprint complete)

### Terry — Contrast Fix & Footer CC License
- `$ink-light` darkened from `#7a6650` → `#6a5542` in `_custom.scss` — WCAG AA contrast failure resolved (~4.8:1 on parchment bg)
- CC license added to global site footer via Hugo partial override at `hugo-site/layouts/_partials/docs/inject/footer.html`
- Finding #004 (Mermaid/Asciinema) investigated and closed: JS loads on-demand via shortcodes only; not used by any content; inert

### Lila — All Three Timelines Rebuilt as Native Hugo Content
- `timelines/pre-war-timeline.md` — 8 entries, c. 1700s Wales through 1776 enlistment
- `timelines/revolutionary-war-timeline.md` — 13 entries, Greenwich Tea Burning through 1787 Constitution ratification; Lewis Howell death date discrepancy documented with caveat
- `timelines/post-war-timeline.md` — 9 entries, 1779 resignation through 1802 death
- Timeline visual CSS added to `_custom.scss`: left-border rail, gold diamond markers, red date headers

### Lila — Biography Section Fully Expanded
- `biography/_index.md` rewritten from brief overview to full narrative biography
- Sections: Early Life, Military Career (battles, Valley Forge, Lewis's death, intelligence work, resignation), Statesman & Governor (Constitution ratification, six terms, Whiskey Rebellion), The Poet, Death & Legacy
- No longer repeats homepage content — stands as independent scholarly biography
- Internal CC license attribution retained at page footer

### Andrew — Research & Sources Updated
- `Project/research/sources.md` fully rebuilt: primary sources, secondary sources, online resources, archives to contact, open research questions
- Lewis Howell death date discrepancy formally documented with three conflicting accounts (June 5 / June 28 / July 5); resolution path identified; site uses June 5 with caveat pending primary source verification
- Clarence Parvin analysis documented: name is suspicious for 1770s colonial period; cross-reference against *Tea Burners of Cumberland County* recommended
- Patriotic song for Washington documented as open research question (not a launch blocker)

### Security — All Pre-Launch Findings Resolved
- All 8 security findings addressed: 5 fully resolved, 1 partial (SHA pinning), 1 downgraded to inert, 1 verified closed
- Pre-launch security checklist: 6/6 items closed or accepted

### Build Status
- **Hugo build:** 170 pages, 234 static files, 0 errors ✅
- Build confirmed after all changes applied

---

## 2026-03-27 (updated — Terry hired, Lila's workload redistributed)

### Terry Hired as Web Development Assistant
- **Terry** brought on as Lila's assistant to handle routine CSS, content, and build tasks
- Frees Lila to focus on complex architecture, timeline rebuilds, and team coordination
- Terry's immediate assignments (per Lila):
  - Fix `$ink-light` contrast in `_custom.scss` (#7a6650 → #6a5542)
  - Investigate disabling Mermaid/Asciinema JS (Sherlock Finding #004)
  - Add CC license to global site footer
  - Formspree contact form implementation (pending Lila providing endpoint)
- Role definition filed: `roles/role-definitions.md`
- Onboarding document filed: `roles/onboarding-terry.md`
- **Actioned by:** Rebecca (HR Director) per Richard's direction

---

## 2026-03-27 (updated — audits initiated)

### Vincent — Usability & Contrast Audit Filed
- Full audit filed at `Project/design/usability-audit.md`
- **One contrast failure identified:** `$ink-light` (#7a6650) on `$parchment-bg` (~4.1:1) — fails WCAG AA for small text; used in footer and captions at 0.8rem
- Additional usability issues: missing global `:focus-visible` styles, no responsive table overflow, small font sizes in secondary UI
- Portrait of Richard Howell requested for homepage — awaiting file in `Project/incoming/`
- Enhancement opportunities documented for post-launch

### Sherlock — Initial Security Analysis Filed
- Full findings log filed at `Project/security/findings-log.md`
- **8 findings total:** 1 High, 3 Medium, 4 Low/Informational
- 🟠 **HIGH (pre-launch blocker):** Email address `govhowell@thgnetworks.com` exposed in public HTML via Lila's internal note in `contact.md` — must be removed before launch
- 🟡 **MEDIUM:** Hugo version not pinned in CI (should pin to `0.155.2`)
- 🟡 **MEDIUM:** Third-party GitHub Actions not pinned to commit SHAs
- 🟡 **MEDIUM:** Unnecessary JS bundles (Mermaid, Asciinema) loaded on all pages
- 🟢 **LOW/INFO:** `contents: write` permission scope, no CSP, internal notes on public pages, submodule pin verification needed
- Pre-launch security checklist filed in findings log

---

## 2026-03-27

### Two New Team Members Hired
- **Vincent** (Site Artist) — hired to bring artistic quality and period-appropriate visual flair to the site; will collaborate with Lila on asset integration and with Andrew on historical accuracy of visual elements
- **Sherlock** (Security Analyst) — hired to monitor the project and published site for security vulnerabilities and potential exploits; scope includes deployment pipeline, Formspree contact form, Hugo config, and theme dependencies
- Role definitions updated in `roles/role-definitions.md`
- Onboarding documents filed: `roles/onboarding-vincent.md`, `roles/onboarding-sherlock.md`
- **Actioned by:** Rebecca (HR Director) per Richard's direction

---

## 2026-03-26 (updated — homepage rebuilt, site review complete)

### Site Review Conducted
- Full team review of site content and structure
- Meeting minutes filed: `meetings/2026-03-26-site-review.md`

### Homepage Rebuilt (`content/_index.md`)
- Full original landing page content restored in Hugo markdown
- NJ State House circa 1806 image added as hero image
- Vital records and children table added
- "Explore This Site" navigation table added — links to all 7 sections
- "About This Site" + 5th Great Grandsons attribution prominently placed
- CC license moved to page footer
- Contact link corrected to `/resources/contact/`

### Fixes Applied
- Broken contact link (`/contact-us/` → `/resources/contact/`) fixed in biography page
- Andrew's internal research warning box removed from public biography page
- **Build:** 170 pages, 234 static files, 0 errors

### Outstanding (before launch)
- Remaining internal research notes on other public pages — review and remove
- Timeline pages need full rebuild as native Hugo content (Andrew + Lila)
- Contact form Formspree reconfiguration (Lila)
- CC license in global site footer (Lila)
- Biography section needs deeper content, not repeat of homepage (Andrew + Lila)
- Research: identify the patriotic song sung for Washington in Trenton (Andrew)

---

## 2026-03-26 (updated — media migrated)

### Media Files Migrated to hugo-site/static/
- **152 original images** copied to `hugo-site/static/images/`
- **12 PDFs** copied to `hugo-site/static/documents/`
- **525 WordPress-generated resized variants** excluded (not needed — Hugo handles resizing natively)
- **Plugin junk excluded:** bws_captcha_images, bws-custom-code, sucuri folders
- **Hugo build:** 170 pages, 234 static files, 0 errors, 615ms
- **Done by:** Lila

---

## 2026-03-26 (updated — full content migration complete)

### All Pages Migrated — Hugo Build: 170 pages, 0 errors, 131ms

**People section**
- `people/dr-lewis-howell.md` — Surgeon, 2nd NJ Regiment; twin of Richard Howell; died June 5, 1778
- `people/varina-howell-davis.md` — Full biography; First Lady of the Confederacy; four Jefferson Davis letters transcribed in full
- `people/william-howell-1793-1863.md` — Richard's son; War of 1812; father of Varina; includes Oct 22, 1854 Jefferson Davis letter

**Family section**
- `family/howell-family-history.md` — Full transcription of Leach's *Genealogical and Biographical Memorials* (1898), pp. 129–139
- `family/family-tree.md` — Dead WikiTree iframes replaced with direct links (Howell-2982)

**Resources section**
- `resources/homestead.md` — Full HABS survey record for Howell Homestead (NJ0452); 6 drawing images linked
- `resources/maps.md` — All 17 historical maps cataloged in table format
- `resources/documents.md` — All 10 PDFs listed with descriptions and links
- `resources/contact.md` — Contact page; Formspree form flagged for reconfiguration

**Letters section**
- `letters/revolutionary-war-correspondence.md` — Six primary source excerpts from Washington Papers; intelligence role 1778–1780
- `letters/letter-to-shreve-oct-1778.md` — Full 3-page letter transcript in blockquote; scanned pages linked
- `letters/letter-to-benedict-arnold.md` — Full text including two enclosed intelligence reports; pre-treason context noted
- `letters/pre-war-letters.md` — Placeholder (dead TimelineJS embed); Google Sheets key preserved
- `letters/post-war-letters.md` — Placeholder (dead TimelineJS embed)

**Timelines section**
- `timelines/revolutionary-war-timeline.md` — Dead embed documented; Google Sheets key preserved; events listed for rebuild
- `timelines/pre-war-timeline.md` — Dead embed documented; pre-war events outlined
- `timelines/post-war-timeline.md` — Dead embed documented; gubernatorial events outlined

**Key research findings flagged by Andrew:**
- Lewis Howell death date inconsistency: "June 5, 1778" vs. "7 days after Monmouth" (July 5) — needs primary source verification
- Leach (1898) genealogy says Lewis died "on the day of the battle of Monmouth" — contradicts other site pages
- Varina Howell Davis marriage date: Feb 26 vs. Feb 28 — Feb 26 is correct per *Papers of Jefferson Davis*
- All three timeline embeds are dead — Google Sheets keys preserved for Wayback Machine recovery
- WikiTree iframe widgets replaced with direct links

**Outstanding items:**
- 806 media files not yet moved to `hugo-site/static/` (Pam/Lila)
- Timelines need full rebuild as native Hugo content (Andrew + Lila)
- Formspree contact form needs reconfiguration (Lila)

---

## 2026-03-26 (updated — first content migrated)

### Content Migration — First Three Pages
- **`content/biography/_index.md`** — Richard Howell biography page migrated from homepage HTML
- **`content/events/greenwich-tea-burning.md`** — Greenwich Tea Burning page migrated and expanded
- **`content/events/2nd-new-jersey-regiment.md`** — 2nd NJ Regiment page migrated with full roster tables
- **Hugo build:** 43 pages, 107ms, zero warnings
- **Errors corrected by Andrew:**
  - Death year on homepage header: "1803" corrected to **1802**
  - Tea burner name: "Ephriam Nemcomb" corrected to **Ephraim Newcomb**
  - Tea burner name: "Silas Whitekar" corrected to **Whitcar**
- **Research flags raised by Andrew:**
  - "Clarence Parvin" name in tea burners list needs verification
  - 2nd NJ Regiment service record needs expansion beyond Valley Forge Muster Roll
  - Lewis Howell / Richard Howell brother narrative thread — develop further
- **Done by:** Andrew (content), Lila (build/formatting)

---

## 2026-03-26 (updated — theme installed)

### Hugo Book Theme Installed & Configured
- Hugo Book installed as git submodule at `hugo-site/themes/hugo-book`
- `hugo.toml` fully configured: baseURL, theme, Book params, taxonomies, nav menus
- Parchment CSS skin created at `hugo-site/assets/_custom.scss`:
  - Fonts: IM Fell English (headings), Libre Baskerville (body)
  - Colors: aged parchment background, near-black ink, deep red accent links
  - Custom styles: blockquotes for letter transcriptions, decorative HR dividers, dark header bar with gold accent
- GitHub Actions deploy workflow created at `.github/workflows/deploy.yml`
  - Builds from `hugo-site/`, publishes to repo root
  - Clean overwrite — removes old WordPress files on deploy
- **Hugo build test:** PASSED — 23 pages, 107ms
- **Done by:** Lila

---

## 2026-03-26 (updated — theme selected)

### Decision — Hugo Theme
- **Theme selected:** Hugo Book (Option 1)
- **Rationale:** Best navigation structure (persistent tree sidebar); cleanest foundation for custom CSS. Lila will build a parchment skin on top — aged paper aesthetic, period serif typography.
- **Decided by:** Richard (Project Manager)
- **Logged by:** Pam

---

## 2026-03-26 (updated again)

### Hugo Scaffold Created
- **Hugo v0.155.2** confirmed installed (Homebrew, darwin/arm64)
- **`hugo-site/` directory scaffolded** inside repo root
- `hugo.toml` configured: baseURL, title, nav menu, taxonomies (periods, people, events)
- Content sections created: `biography`, `timelines`, `letters`, `events`, `family`, `resources`, `people`
- Archetypes created for: `letters`, `events`, `people`, `timelines`
- `.gitignore` added (excludes `public/`, `resources/_gen/`, `.hugo_build.lock`)
- **Theme:** not yet selected — Lila presenting options
- **Done by:** Lila

---

## 2026-03-26 (updated)

### Decision — Repository Strategy
- **Decision:** The existing GitHub repository will be kept. The new Hugo site will be developed in a `hugo-site/` subdirectory within the current repo. At publish time, the Hugo-generated output will overwrite the existing WordPress HTML files in the root. One repo, one source of truth.
- **Decided by:** Richard (Project Manager)
- **Logged by:** Pam

---

## 2026-03-26

### Project Kickoff
- **Project formally initiated** by Richard (Project Manager)
- **Team assembled:** Richard, Rebecca, Andrew, Lila, Pam
- **Pam hired** as Project Admin by Rebecca
- **Project folder structure created** at `govhowell.org/Project/`
- **Technology decision:** Hugo selected as static site generator (pending final theme selection by Lila)
- **Kickoff meeting held** — minutes filed at `meetings/2026-03-26-kickoff-meeting.md`
- **Role definitions drafted** by Rebecca — filed at `roles/role-definitions.md`

### Initial Site Assessment
- Existing site: WordPress HTML export (static dump)
- **29 HTML pages** identified, **0 markdown files**, **806 media files** in uploads
- Content sections identified: timelines, letters, biographies, family tree, maps, documents, blog
- Full audit delegated to Andrew (content) and Lila (structure)

---

*Log started: 2026-03-26 | Maintained by Pam*
