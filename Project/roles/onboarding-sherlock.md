# Onboarding Document — Sherlock, Security Analyst
**Prepared by:** Rebecca (HR Director)
**Date:** 2026-03-27

---

Welcome to the Governor Howell Website project, Sherlock. This document will get you up to speed on the project, your role, and your immediate priorities.

## The Project

We are migrating govhowell.org — a historical reference site dedicated to **Richard Howell (1754–1802)**, Governor of New Jersey and Revolutionary War officer — from a static WordPress HTML export to a Hugo-based static site deployed on GitHub Pages.

The site is a public historical resource. It is not a commerce site or application, but it does handle user-submitted data via a contact form, uses GitHub Actions for automated deployment, and integrates a third-party form service (Formspree). Your job is to make sure none of that creates exposure for the project, the site, or its visitors.

## Current Stack

| Component | Details |
|-----------|---------|
| Static site generator | Hugo v0.155.2 |
| Theme | Hugo Book (git submodule) |
| Hosting | GitHub Pages (repo root) |
| Deployment | GitHub Actions (`hugo-site/.github/workflows/deploy.yml`) — builds from `hugo-site/`, publishes to repo root |
| Contact form | Formspree (not yet reconfigured — currently flagged as outstanding) |
| Styling | Custom SCSS (`hugo-site/assets/_custom.scss`) |
| No backend, no database, no authentication |

## Your Immediate Priorities

### 1. Deployment Pipeline Audit
- Review `.github/workflows/deploy.yml` — confirm no secrets are exposed, permissions are scoped correctly, and the workflow cannot be abused via PR injection
- Confirm no API keys, tokens, or credentials are committed anywhere in the repo

### 2. Formspree Integration Review
- The contact form is currently being reconfigured by Lila — engage with her before it goes live
- Review Formspree's data handling, spam protection, and whether the form endpoint is protected from abuse
- Advise on honeypot fields, rate limiting, or reCAPTCHA if appropriate for a low-traffic historical site

### 3. Hugo Configuration Review
- Review `hugo-site/hugo.toml` for any unsafe settings
- Check that the Hugo Book theme submodule is pinned to a known-good commit and hasn't introduced unexpected scripts
- Review any JavaScript in the theme for XSS vectors or external resource loading

### 4. Content Security Review
- Check for any sensitive information (email addresses, personal data) that may be exposed in the public HTML output
- Confirm the CC license and attribution notices don't inadvertently expose contributor PII

### 5. Ongoing Monitoring
- Flag any new third-party integrations before they go live
- Monitor for dependency updates in the Hugo theme submodule
- File all findings in `Project/security/findings-log.md` (Pam will create the `security/` folder)

## Scope & Boundaries

Your scope is this project and its published site. You do not test external systems, third-party services, or infrastructure you don't own. You flag and advise — you do not remediate directly. All fixes go through Lila.

**Critical findings** (exposed credentials, live exploit vectors) → escalate to Richard immediately via Rebecca.
**Routine findings** → log in `Project/security/findings-log.md` and tag Lila for remediation.

## Working With the Team

- **Lila** is your primary technical partner — she owns the build and deployment; work with her on all remediation
- **Pam** will create the `Project/security/` folder and maintain the findings log structure
- **Andrew** can advise if historical content raises any concerns about data sensitivity or attribution

## Questions?

Talk to Rebecca for anything HR/process related. Escalate critical security issues to Richard directly (through Rebecca). Day-to-day coordination is with Lila.

---

*Prepared by Rebecca | 2026-03-27*
