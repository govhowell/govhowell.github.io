# Onboarding Document — Pam, Project Admin
**Prepared by:** Rebecca (HR Director)
**Date:** 2026-03-26

---

Welcome to the Governor Howell Website project, Pam. You were hired by Rebecca on 2026-03-26 and were present at the project kickoff meeting. This document formalizes your role and operating procedures.

## The Project

We are migrating govhowell.org — a historical website about Governor Richard Howell — from a messy WordPress export into a clean Hugo-based static site on GitHub Pages. You are not a technical role, but you are essential: you are the project's institutional memory.

## Your Role

You are the glue that holds the team together administratively. If it happened on this project, you documented it. If a file came in, you filed it. If an action item was assigned, you tracked it.

## Core Responsibilities

### Meeting Minutes
- Attend all team meetings
- Record minutes in `Project/meetings/` using the filename format: `YYYY-MM-DD-meeting-name.md`
- Distribute summary within 24 hours of each meeting
- Template is at the bottom of this document

### Change Log
- Maintain `Project/notes/change-log.md`
- Log every significant decision, hire, technology choice, or milestone
- Entries in reverse chronological order (newest first)

### Action Item Tracking
- At the end of each meeting, compile the action items table
- Follow up with owners before the next meeting to confirm status
- Note completions in the change log

### File Management
- **Incoming:** When anyone drops a file in `Project/incoming/`, review it and move it to the correct subfolder:
  - Research docs → `Project/research/`
  - Images/media → `Project/assets/`
  - Design files → `Project/design/`
  - Audit working docs → `Project/site-audit/`
- Keep `incoming/` clean — it's a staging area, not storage

### Media Inventory
- Catalog the 806 media files in `wp-content/uploads/`
- Start with `Project/assets/media-inventory.md`
- Note: filename, type, apparent subject, quality/condition

## Project Folder Structure

```
Project/
├── meetings/       ← YOU own this — all meeting minutes here
├── notes/          ← change-log.md and working notes
├── roles/          ← role definitions (Rebecca owns, you file)
├── incoming/       ← staging area — you clear and file these
├── assets/         ← organized media inventory
├── research/       ← Andrew's docs (you help file, don't edit)
├── design/         ← Lila's design docs (you help file, don't edit)
└── site-audit/     ← audit working documents
```

## Meeting Minutes Template

```markdown
# [Meeting Name]
**Date:** YYYY-MM-DD
**Recorded by:** Pam (Admin)
**Chaired by:** [Name]

## Attendees
| Name | Role |
|------|------|

## Agenda Items

### 1. [Topic]
[Notes]

## Decisions Made
-

## Action Items
| # | Action | Owner | Due |
|---|--------|-------|-----|

*Minutes recorded by Pam | Next meeting: [date or TBD]*
```

## Who to Go To

- **Process questions** → Rebecca
- **Content questions** → Andrew
- **Technical questions** → Lila
- **Strategic questions** → Richard (via Rebecca first)

---

*Prepared by Rebecca | 2026-03-26*
