# Governor Howell Website — Project Management

**Project Manager:** Richard
**Started:** 2026-03-26
**Goal:** Migrate govhowell.org from a WordPress HTML export to a Hugo-based static site deployable on GitHub Pages.

---

## Team

| Name | Role |
|------|------|
| Richard | Project Manager |
| Rebecca | HR Director |
| Andrew | Chief Researcher & Historian |
| Lila | Chief Web Designer & Architect |
| Pam | Project Admin |
| Vincent | Site Artist |
| Sherlock | Security Analyst |
| Terry | Web Development Assistant (Lila's Assistant) |

---

## Folder Structure

```
Project/
├── README.md                   ← You are here
├── meetings/                   ← All meeting minutes (Pam)
├── notes/
│   └── change-log.md           ← Running log of decisions and milestones
├── roles/
│   ├── role-definitions.md     ← Official role descriptions (Rebecca)
│   ├── onboarding-andrew.md
│   ├── onboarding-lila.md
│   └── onboarding-pam.md
├── incoming/                   ← Drop new files here; Pam will file them
├── assets/
│   └── media-inventory.md      ← Catalog of wp-content/uploads/ (Pam)
├── research/
│   └── sources.md              ← Source inventory (Andrew)
├── design/
│   └── theme-options.md        ← Hugo theme research (Lila)
└── site-audit/
    ├── content-audit.md        ← Historical content review (Andrew)
    └── structure-audit.md      ← Site architecture review (Lila)
```

---

## Current Status

**Phase:** LIVE ✅
**Deployed:** 2026-03-27
**URL:** https://govhowell.org
**Repository:** github.com/govhowell/govhowell.github.io

The site is fully deployed on GitHub Pages. Any push to `master` triggers an automatic Hugo build and deploy via GitHub Actions. See `notes/change-log.md` for full history and outstanding items.

---

## Quick Links

- [Kickoff Meeting Minutes](meetings/2026-03-26-kickoff-meeting.md)
- [Usability Audit](design/usability-audit.md)
- [Security Findings Log](security/findings-log.md)
- [Role Definitions](roles/role-definitions.md)
- [Change Log](notes/change-log.md)
- [Content Audit](site-audit/content-audit.md)
- [Structure Audit](site-audit/structure-audit.md)
