# govhowell.org — Site Rebuild Guide

**Author:** Lila (Chief Web Designer & Architect)
**Date:** 2026-03-27
**Purpose:** Complete description of the site such that it can be rebuilt from scratch if needed.

---

## Overview

govhowell.org is a Hugo-based static site about Governor Richard Howell (1754–1802) of New Jersey. It was migrated from a WordPress HTML export in March 2026. The site is hosted on GitHub Pages, built automatically by GitHub Actions on every push to the `master` branch.

---

## Repository

- **GitHub:** `github.com/govhowell/govhowell.github.io`
- **Default branch:** `master` (Hugo source)
- **Deploy branch:** `gh-pages` (built output — auto-generated, do not edit)
- **Custom domain:** `govhowell.org` (CNAME record; `CNAME` file at repo root)

---

## Technology Stack

| Component | Choice | Version / Notes |
|-----------|--------|-----------------|
| Static site generator | Hugo (extended) | v0.155.2 — pinned, do not change to `latest` |
| Theme | Hugo Book | Vendored at `themes/hugo-book/`, pinned to commit `751bde097bc9` |
| CSS preprocessor | SCSS | Required — use Hugo extended build only |
| Hosting | GitHub Pages | Serves from `gh-pages` branch |
| CI/CD | GitHub Actions | `.github/workflows/deploy.yml` |
| Deploy action | peaceiris/actions-gh-pages@v4 | Pushes built output to `gh-pages` |

---

## Repository Structure

```
govhowell.github.io/          ← repo root = Hugo site root
├── .github/
│   └── workflows/
│       └── deploy.yml        ← CI/CD pipeline
├── .gitignore
├── .nojekyll                 ← prevents GitHub's Jekyll builder from running
├── .gitmodules               ← comment-only; theme is vendored, not a submodule
├── CNAME                     ← contains: govhowell.org
├── archetypes/               ← Hugo content templates
├── assets/
│   └── _custom.scss          ← ALL custom CSS lives here (parchment skin)
├── content/                  ← all site content in Markdown
│   ├── _index.md             ← homepage
│   ├── biography/
│   ├── timelines/
│   ├── letters/
│   ├── events/
│   ├── family/
│   ├── people/
│   └── resources/
├── hugo.toml                 ← Hugo configuration
├── layouts/
│   ├── baseof.html           ← overrides theme baseof to move banner above <main>
│   ├── _partials/
│   │   └── docs/inject/
│   │       ├── body.html     ← currently empty
│   │       └── footer.html   ← global CC license footer
│   └── _shortcodes/
│       ├── portrait.html     ← {{< portrait src="" alt="" caption="" >}}
│       ├── site-banner.html  ← {{< site-banner >}}
│       └── timeline.html     ← {{< timeline >}}...{{< /timeline >}}
├── static/
│   ├── images/               ← all site images (152 originals)
│   └── documents/            ← all PDFs (12 files)
├── themes/
│   └── hugo-book/            ← vendored theme (do not modify)
├── start_webserver.sh        ← local dev server script
└── Project/                  ← team project management files (not part of site)
```

---

## Hugo Configuration (`hugo.toml`)

Key settings:
- `baseURL = 'https://govhowell.org/'`
- `theme = 'hugo-book'`
- `enableRobotsTXT = true`
- `enableGitInfo = false`
- Goldmark renderer runs in **safe mode** (no `unsafe = true`) — raw HTML in markdown is stripped; use shortcodes instead

---

## Custom Parchment Skin (`assets/_custom.scss`)

All visual customisation is in this single file. Key design decisions:

**Color palette:**
```scss
$parchment-bg: #f5efe0;    // aged paper background
$ink-dark:     #2c1f0e;    // near-black for headings, brand text
$ink-light:    #6a5542;    // body text (darkened for WCAG AA — do not lighten)
$accent-red:   #8b2222;    // links, date headers in timelines
$accent-gold:  #9a7c3a;    // borders, timeline markers
```

**Typography:**
- Headings: IM Fell English (Google Fonts — period serif)
- Body: Libre Baskerville (Google Fonts — legible serif)

**Background:**
- Full-page fixed newspaper background: `static/images/background.png` (Massachusetts Spy colonial newspaper)
- Applied as `background-image: url('/images/background.png')` with `background-attachment: fixed; background-size: cover`

**Sidebars (left nav + right TOC):**
- `rgba(245, 239, 224, 0.40)` with `backdrop-filter: blur(3px) brightness(1.08)` — frosted vellum effect
- Nav links use `text-shadow` halo for readability against the newspaper background

**Content panel:**
- Solid `$parchment-bg` background with `box-shadow: 0 4px 32px rgba(20, 12, 4, 0.55)`

**Custom classes defined:**
- `.portrait-frame` — double-rule border, gold outline, period drop-shadow
- `.portrait-caption` — italic IM Fell English
- `.site-banner` — full-width banner with bleed margins
- `.site-license` — CC license footer
- `.timeline` — left-border rail with gold diamond markers and red date headers

---

## Layout Overrides

### `layouts/baseof.html`
Overrides the theme's baseof to move `{{ partial "docs/inject/body" . }}` **before** `<main class="container flex">` instead of before `</body>`. This is required for the site banner to appear at the top of the content area rather than the bottom of the page.

### `layouts/_partials/docs/inject/footer.html`
Injects the global Creative Commons BY-NC 4.0 license notice into every page footer.

### `layouts/_partials/docs/inject/body.html`
Currently empty. Previously held the site banner before it was moved to the homepage shortcode.

---

## Shortcodes

All shortcodes are in `layouts/_shortcodes/`. Raw HTML is **not** permitted in content markdown (goldmark safe mode) — these shortcodes are the mechanism for HTML injection.

### `{{< portrait src="" alt="" caption="" >}}`
Renders the framed portrait image. Used on the homepage.

### `{{< site-banner >}}`
Renders `static/images/rbhbanner2.png` (historical masthead — map, battle scene, portrait). Used at the top of the homepage content.

### `{{< timeline >}}...{{< /timeline >}}`
Wraps timeline entries in the styled `.timeline` div. Used in all three timeline pages. The inner content is standard markdown rendered with `markdownify`.

---

## Content Sections

| Section | Path | Pages | Notes |
|---------|------|-------|-------|
| Homepage | `content/_index.md` | 1 | Banner, portrait, intro, navigation table |
| Biography | `content/biography/_index.md` | 1 | Full narrative biography — 6 sections |
| Timelines | `content/timelines/` | 4 | Index + 3 period timelines (native Hugo) |
| Letters | `content/letters/` | 6 | Index + 5 letter/correspondence pages |
| Events | `content/events/` | 3 | Index + Greenwich Tea Burning + 2nd NJ Regiment |
| Family | `content/family/` | 3 | Index + family tree + Howell family history |
| People | `content/people/` | 4 | Index + Lewis Howell + Varina Davis + William Howell |
| Resources | `content/resources/` | 5 | Index + homestead + maps + documents + contact |

**Total:** 170 pages (including theme-generated tag/taxonomy pages)

---

## CI/CD Pipeline (`.github/workflows/deploy.yml`)

Trigger: push to `master` or manual `workflow_dispatch`

Steps:
1. `actions/checkout@v4` — checks out `master`
2. `peaceiris/actions-hugo@v3` — installs Hugo v0.155.2 extended
3. `hugo --minify --gc` — builds site into `public/`
4. `peaceiris/actions-gh-pages@v4` — pushes `public/` to `gh-pages` branch with `force_orphan: true`, sets CNAME

**GitHub Pages** is configured to serve from the `gh-pages` branch (root).

**⚠ Action version warning:** All three actions run on Node.js 20, which is deprecated on GitHub runners from June 2, 2026. Update action versions before that date.

---

## Local Development

```bash
./start_webserver.sh
```

Runs Hugo dev server at `http://localhost:1313` with drafts, future posts, fast render disabled, and auto-navigate on change. Requires Hugo v0.155.2 extended (`brew install hugo`).

---

## How to Rebuild from Scratch

1. **Clone the repo:** `git clone git@github.com:govhowell/govhowell.github.io.git`
2. **Install Hugo:** `brew install hugo` (verify `hugo version` shows 0.155.2 extended or later)
3. **Local preview:** `./start_webserver.sh` → open `http://localhost:1313`
4. **Edit content:** files in `content/` — standard Hugo markdown with TOML front matter
5. **Edit styles:** `assets/_custom.scss` — SCSS, auto-compiled by Hugo extended
6. **Deploy:** `git push origin master` → GitHub Actions builds and deploys automatically

**To rebuild the repo from zero:**
- Start with `hugo new site .` in an empty directory
- Copy in `themes/hugo-book/` (or `git submodule add https://github.com/alex-shpak/hugo-book themes/hugo-book` and pin to `751bde097bc9`)
- Restore `hugo.toml`, `assets/_custom.scss`, `layouts/`, `content/`, `static/` from backup
- Add `.nojekyll`, `CNAME`, `.github/workflows/deploy.yml`
- Push to GitHub; configure Pages to serve from `gh-pages`

---

## Known Issues / Open Items

| Item | Owner | Priority |
|------|-------|----------|
| Formspree contact form — not yet configured for govhowell.org | Lila | Medium |
| Lewis Howell death date — three conflicting sources | Andrew | Medium |
| Clarence Parvin — name verification needed | Andrew | Low |
| GitHub Actions Node.js 20 deprecation (deadline: 2026-06-02) | Lila | Medium |
| Action SHA pinning (security hardening) | Sherlock/Lila | Low |

---

*Document prepared by Lila — 2026-03-27*
