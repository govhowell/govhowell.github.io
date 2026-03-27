# Security Findings Log — Governor Howell Website
**Maintained by:** Sherlock (Security Analyst)
**Date Initiated:** 2026-03-27
**Scope:** Hugo build configuration, GitHub Actions deployment pipeline, third-party integrations, published content, and repository hygiene

---

> Findings are rated: 🔴 **Critical** | 🟠 **High** | 🟡 **Medium** | 🟢 **Low / Informational**
> Remediation owner is Lila unless otherwise noted.

---

## Finding #001 — 🟠 High | Email Address Exposed in Public HTML

**File:** `hugo-site/content/resources/contact.md` (line 21)
**Status:** ✅ RESOLVED — 2026-03-27 (Lila)
**Details:** Lila's internal developer note uses a `[!NOTE]` admonition block which Hugo Book renders as a visible callout on the live public page. This note contains the plaintext email address `govhowell@thgnetworks.com`. This address will be scraped by bots and added to spam lists.

**Recommended remediation:**
- Remove the entire `[!NOTE]` admonition block from `contact.md` before launch
- Move Lila's notes to an internal project file (e.g., `Project/notes/contact-form-notes.md`)
- Never store email addresses in content files that will be rendered publicly

**Escalation:** Flag to Lila immediately — this is a pre-launch blocker.

---

## Finding #002 — 🟡 Medium | Hugo Version Not Pinned in CI

**File:** `hugo-site/.github/workflows/deploy.yml` (line: `hugo-version: 'latest'`)
**Status:** ✅ RESOLVED — 2026-03-27 (Lila). Pinned to `'0.155.2'`.
**Details:** The GitHub Actions workflow installs whatever Hugo version is current at build time (`hugo-version: 'latest'`). This means a Hugo release could introduce breaking changes or a security patch could go unapplied if the build caches an old runner image. It also means the build is not reproducible.

**Recommended remediation:**
- Pin to a specific Hugo version: `hugo-version: '0.155.2'` (the version confirmed working per change log)
- Update the pinned version intentionally when upgrading

---

## Finding #003 — 🟡 Medium | Third-Party GitHub Actions Not Pinned to SHA

**File:** `hugo-site/.github/workflows/deploy.yml`
**Status:** ⚠️ PARTIALLY RESOLVED — 2026-03-27 (Lila). TODO comments and SHA lookup instructions added to workflow. Full SHA pinning requires manual verification against release history — flagged for next maintenance pass.
**Details:** The workflow uses:
- `peaceiris/actions-hugo@v3`
- `peaceiris/actions-gh-pages@v4`

Version tags (`@v3`, `@v4`) can be moved by the action author to point at different commits. A compromised or updated action at the same tag could execute arbitrary code in the deployment pipeline with `contents: write` permissions.

**Recommended remediation:**
- Pin both actions to their full commit SHA:
  ```yaml
  uses: peaceiris/actions-hugo@75d2a84952bfd8ef7ee63cbafc493a9f982e2c00  # v3.10.0
  uses: peaceiris/actions-gh-pages@4f9cc6602d3f66b9c108549d231e62369c1bc9a7  # v4.0.0
  ```
- Verify the SHA against the action's release history before using

---

## Finding #004 — 🟡 Medium | Unnecessary JS Bundles Loaded on All Pages

**File:** `hugo-site/public/` (built output)
**Status:** ✅ RESOLVED — 2026-03-27. Upon full investigation, Mermaid and Asciinema JS are loaded **on-demand only** when their shortcodes (`{{< mermaid >}}`, `{{< asciinema >}}`) are called in content. Since no content on this site uses those shortcodes, the JS files are never referenced in any page's HTML. The files exist in `static/` as theme assets but are inert. No remediation needed. Downgraded to informational.
**Details:** The Hugo Book theme includes JavaScript for features not used by this site:
- `mermaid.min.js` — diagram rendering (no diagrams on this site)
- `asciinema/asciinema-player.min.js` and `asciinema-auto.js` — terminal recordings (not used)
- Multiple stale `en.search.min.*.js` files — old search index versions, possibly from repeated builds

These add unnecessary attack surface and page weight. Mermaid.js in particular has had past XSS vulnerabilities when rendering untrusted input.

**Recommended remediation:**
- In `hugo.toml`, disable Mermaid and Asciinema if Hugo Book provides config toggles: check for `BookMermaid`, `BookAsciinema` params
- Run `hugo --gc` (garbage collect) to remove stale search index files — the `--gc` flag is already in the deploy workflow but old files in `public/` may be from local builds
- Add `public/` to `.gitignore` if not already present (built output should not be committed)

---

## Finding #005 — 🟢 Low | `permissions: contents: write` Is Broader Than Necessary

**File:** `hugo-site/.github/workflows/deploy.yml`
**Status:** Informational
**Details:** The workflow sets `permissions: contents: write` which grants write access to all repository contents. The actual requirement is write access to push the built site to the `main` branch. While this is the standard approach for `peaceiris/actions-gh-pages`, it is worth documenting as an accepted risk.

**Recommended remediation:**
- Consider using GitHub Pages' native deployment mechanism (`actions/deploy-pages`) which uses a dedicated `pages: write` permission scope — narrower and purpose-built for Pages deployments
- OR document this as an accepted risk with a comment in the workflow file

---

## Finding #006 — 🟢 Low | No Content Security Policy

**File:** Site-wide
**Status:** Informational
**Details:** GitHub Pages does not support custom HTTP headers, so a server-side CSP cannot be set. There is currently no `<meta http-equiv="Content-Security-Policy">` in the theme head templates either. The site loads resources from:
- Google Fonts CDN (external)
- All other assets are local

Without a CSP, if any content injection were possible (e.g., via user-contributed content in the future), there would be no browser-enforced mitigation.

**Recommended remediation:**
- Add a meta CSP tag to the Hugo theme's head partial. Minimum:
  ```html
  <meta http-equiv="Content-Security-Policy"
    content="default-src 'self'; style-src 'self' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; script-src 'self'; img-src 'self' data:;">
  ```
- This is low priority for a static read-only site with no user authentication, but good hygiene

---

## Finding #007 — 🟢 Low | Internal Research Notes Potentially Visible on Public Pages

**File:** Multiple content files (per change log: "remaining internal research notes on other public pages")
**Status:** ✅ RESOLVED — 2026-03-27 (Lila). All 18 content files containing `[!NOTE]` internal blocks swept. Notes converted to HTML comments (stripped by Hugo's goldmark renderer in safe mode — absent from built HTML output). Research content preserved in source for developer reference.
**Details:** The change log notes that internal research notes (similar to the Lila note in contact.md) may exist on other public-facing pages. These could expose working commentary, researcher names, or internal project context to the public.

**Recommended remediation:**
- Andrew and Lila to complete a pass of all content files before launch, removing any internal notes or admonition blocks
- Establish a convention: internal notes go in `Project/` only, never in `hugo-site/content/`

---

## Finding #008 — 🟢 Low | Hugo Book Theme Submodule — Verify Pinned to Commit

**File:** `.gitmodules` / `hugo-site/themes/hugo-book/`
**Status:** ✅ RESOLVED — verified 2026-03-27. Submodule is pinned to commit `751bde097bc9288666305bdb10c73e491fc43a72` (tagged v13). Not tracking a branch head.
**Details:** If the Hugo Book submodule points to a branch (e.g., `master`) rather than a specific commit SHA, any upstream change to the theme could affect the next build. This could introduce unexpected JS, changed templates, or broken CSS.

**Recommended remediation:**
- Run `git submodule status` to verify the submodule is pinned to a specific commit, not tracking a branch head
- If tracking a branch, pin it: `cd hugo-site/themes/hugo-book && git checkout <specific-commit-sha>`

---

## Pre-Launch Security Checklist

- [x] Finding #001: Remove exposed email from `contact.md` ✅
- [x] Finding #002: Pin Hugo version in workflow ✅
- [x] Finding #003: Pin action SHAs in workflow ⚠️ partial — SHA lookup TODO remains
- [x] Finding #004: Mermaid/Asciinema JS — investigated, not loaded on any pages ✅ (inert)
- [x] Finding #007: Audit all content files for internal notes ✅
- [x] Finding #008: Verify submodule is pinned to commit ✅

---

*Initiated by Sherlock | 2026-03-27 | Filed in `Project/security/`*
