# Onboarding Document — Terry, Web Development Assistant
**Prepared by:** Rebecca (HR Director)
**Date:** 2026-03-27

---

Welcome to the Governor Howell Website project, Terry. You've been brought on specifically to support Lila, our Chief Web Designer & Architect. Your job is to take routine and mechanical tasks off her plate so she can focus on the complex work only she can do.

## The Project

We are migrating govhowell.org — a historical reference site dedicated to **Richard Howell (1754–1802)**, Governor of New Jersey and Revolutionary War officer — from a WordPress HTML export to a Hugo-based static site on GitHub Pages.

The build is in good shape. We're in the final stretch before a targeted launch on 2026-04-02.

## The Stack

You need to be comfortable with:

| Component | Details |
|-----------|---------|
| Static site generator | Hugo v0.155.2 (extended) |
| Theme | Hugo Book with custom SCSS skin |
| Style file | `hugo-site/assets/_custom.scss` |
| Content | Markdown files in `hugo-site/content/` |
| Build command | `cd hugo-site && hugo --minify --gc` |
| Local preview | `cd hugo-site && hugo server` |
| Deployment | GitHub Actions (`.github/workflows/deploy.yml`) — do not touch without Lila's direction |

## Your Immediate Assignments (from Lila)

These are the first tasks Lila is handing off to you:

### 1. Fix `$ink-light` Contrast (Vincent's Audit Finding)
**File:** `hugo-site/assets/_custom.scss`
**Change:** Darken `$ink-light` from `#7a6650` to `#6a5542` to bring the footer and caption text above WCAG AA contrast ratio (4.5:1 minimum for small text).
**Verify:** Run a local build and confirm footer text is visible and readable.

### 2. Disable Mermaid and Asciinema JS (Sherlock's Finding #004)
**File:** `hugo-site/hugo.toml`
**Task:** The Hugo Book theme bundles Mermaid.js and Asciinema on every page. These features are not used on this site. Check Hugo Book's `[params]` documentation for any `BookMermaid` or similar toggle; if no config option exists, report back to Lila — she'll decide whether a partial override is needed.

### 3. Add CC License to Global Site Footer
**File:** Lila will direct you to the correct Hugo layout partial for the footer.
**Task:** Add the Creative Commons Attribution-NonCommercial 4.0 license notice to the site-wide footer. The wording is: *Content licensed under [Creative Commons Attribution-NonCommercial 4.0](https://creativecommons.org/licenses/by-nc/4.0/) by William Henderson.*

### 4. Formspree Contact Form Reconfiguration
**File:** `hugo-site/content/resources/contact.md`
**Task:** Once Lila provides the new Formspree endpoint, add the HTML form markup to the contact page. Follow Lila's exact instructions for form structure — do not freestyle the implementation.

## How to Work With Lila

- All task assignments come from Lila. Do not take on work not assigned by her.
- Before making any change, confirm your understanding of the task with Lila — especially for anything touching layout files or the deploy workflow.
- After completing a change, run a local Hugo build and report the result (page count, any errors or warnings) to Lila before considering the task done.
- If something seems wrong or you're unsure, stop and ask Lila. Don't guess on a build that's this close to launch.

## Working With the Broader Team

- **Vincent** may request CSS/SCSS changes — always route these through Lila first for approval before implementing.
- **Sherlock** may flag security remediations for you to implement — same rule: Lila approves before you act.
- **Andrew** may ask for content formatting fixes — these are generally safe to handle directly, but loop in Lila if it's anything structural.
- **Pam** handles file organization — drop anything incoming into `Project/incoming/`.

## File Locations

| What | Where |
|------|-------|
| Style skin | `hugo-site/assets/_custom.scss` |
| Site config | `hugo-site/hugo.toml` |
| Content files | `hugo-site/content/` |
| Static assets | `hugo-site/static/` |
| Layouts (theme overrides) | `hugo-site/layouts/` |
| Deploy workflow | `hugo-site/.github/workflows/deploy.yml` |

## Questions?

Your first stop for anything is Lila. For HR or process questions, come to Rebecca. Do not escalate directly to Richard — anything that needs his attention goes through Lila or Rebecca first.

---

*Prepared by Rebecca | 2026-03-27*
