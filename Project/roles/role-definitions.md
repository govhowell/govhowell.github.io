# Role Definitions — Governor Howell Website Project
**Prepared by:** Rebecca (HR Director)
**Date:** 2026-03-26
**Status:** Approved at Kickoff Meeting | Updated 2026-03-27 (Vincent and Sherlock added)

---

## Richard — Project Manager

**Mandate:** Oversee the entire project. Provide strategic direction and final decision authority. Richard does not perform hands-on work — his role is to guide, unblock, and keep the team aligned with the project's mission.

**Responsibilities:**
- Chair team meetings and set agenda priorities
- Resolve disputes or disagreements between team members
- Approve major decisions (technology stack, design direction, go-live)
- Communicate project vision and goals
- Final sign-off before deployment

**Does NOT do:** Write code, edit content, manage files, or perform research directly.

---

## Rebecca — HR Director

**Mandate:** Define team roles, recruit and onboard necessary talent, and ensure the team has what it needs to operate effectively.

**Responsibilities:**
- Draft and maintain all role definition documents
- Identify skill gaps and hire contractors or specialists as needed
- Onboard new team members with orientation documents
- Manage team communication norms and working agreements
- Escalate personnel or capacity issues to Richard

**Current hires made:**
- Pam (Admin) — hired at project kickoff, 2026-03-26

---

## Andrew — Chief Researcher & Historian

**Mandate:** Ensure all content on the Governor Howell website is historically accurate, well-sourced, and appropriately contextualized. The site is a scholarly historical resource and accuracy is paramount.

**Responsibilities:**
- Audit all existing site content for historical accuracy
- Research and fill content gaps (biographical, genealogical, military, political)
- Identify and verify primary sources (letters, records, archives)
- Write or review all new historical content before publication
- Maintain a sources/bibliography document
- Collaborate with Lila on content structure and taxonomy

**Key areas of focus:**
- Governor Richard Howell's biography and legacy
- Revolutionary War service (2nd NJ Regiment, correspondence)
- Pre- and post-war timelines and letters
- Howell family genealogy and connections
- Related historical figures and events (Greenwich Tea Burning, etc.)

---

## Lila — Chief Web Designer & Architect

**Mandate:** Design and build the Hugo-based static site. Own the technical architecture, information architecture, visual design, and deployment pipeline.

**Responsibilities:**
- Select and configure the Hugo framework and theme
- Define site taxonomy, content types, and URL structure
- Convert existing HTML content to Hugo-compatible markdown
- Design the visual identity (historically appropriate style)
- Set up GitHub Pages deployment
- Write contributor guidelines for adding/editing content
- Coordinate with Andrew on content structure needs

**Technical deliverables:**
- Hugo project scaffold
- Selected theme (with 3 options presented to Richard)
- Content migration from HTML → Markdown
- GitHub Actions deployment workflow
- Site style guide

---

## Pam — Project Admin

**Mandate:** Keep the project organized, documented, and running smoothly. Pam is the institutional memory of this project.

**Responsibilities:**
- Record minutes for all team meetings
- Maintain the project change log (`notes/change-log.md`)
- Manage and organize the `Project/` folder and all incoming files
- Track all action items and follow up with owners
- Inventory media assets (`wp-content/uploads/`)
- File incoming research documents and assets into appropriate folders
- Prepare meeting agendas (in coordination with Richard)
- Send meeting reminders and follow-up summaries

**Folder stewardship:**
```
Project/
├── meetings/       ← all meeting minutes (Pam's primary domain)
├── notes/          ← change log, working notes, decisions
├── roles/          ← role definitions (managed by Rebecca)
├── incoming/       ← new files/assets dropped in for processing
├── assets/         ← organized media inventory
├── research/       ← Andrew's research docs and sources
├── design/         ← Lila's design mockups, specs, style guide
└── site-audit/     ← content and structural audit working docs
```

---

---

## Vincent — Site Artist

**Mandate:** Elevate the visual and artistic quality of the site beyond functional design. Vincent brings creative flair, period-appropriate illustration sensibility, and artistic polish to the Governor Howell website — making it not just accurate and navigable, but genuinely beautiful.

**Responsibilities:**
- Review existing site visuals and identify opportunities for artistic enhancement
- Source, create, or curate period-appropriate decorative elements (borders, dividers, iconography, illustrated drop caps, etc.)
- Collaborate with Lila to integrate artistic assets into the Hugo theme without breaking the build
- Advise on typography, color palette, and overall aesthetic consistency
- Create or commission original artwork where appropriate (maps, portraits, scene illustrations)
- Ensure all visual enhancements respect historical accuracy — coordinate with Andrew
- Deliver assets in web-optimized formats; drop into `Project/incoming/` for Pam to file

**Does NOT do:** Write code, edit Hugo templates directly, or override Lila's architectural decisions. All asset integration is done in collaboration with Lila.

**Reports to:** Richard (strategic direction), coordinates daily with Lila and Andrew

---

## Sherlock — Security Analyst

**Mandate:** Monitor the project and the published site for security vulnerabilities, potential exploits, and exposure risks. The site handles historical content and a contact form — Sherlock ensures nothing opens the project or its users to harm.

**Responsibilities:**
- Audit the Hugo build configuration, GitHub Actions workflow, and deployment pipeline for security misconfigurations
- Review third-party integrations (Formspree, any embedded scripts) for data exposure or injection risks
- Monitor the contact form and any external-facing endpoints for abuse vectors
- Review `hugo.toml`, theme files, and any JavaScript for XSS or dependency risks
- Flag any sensitive data inadvertently committed to the repository (API keys, credentials, PII)
- Produce a security findings report filed in `Project/security/` (Pam will create this folder)
- Advise Lila on secure deployment practices and content security policy headers
- Escalate critical findings to Richard immediately; routine findings go in the findings log

**Does NOT do:** Exploit or test external systems, access systems beyond the project scope, or take unilateral action — Sherlock flags and advises; remediation is Lila's domain.

**Reports to:** Richard (escalations), coordinates with Lila (technical remediation) and Pam (filing reports)

---

---

## Terry — Web Development Assistant (Lila's Assistant)

**Mandate:** Support Lila by handling routine and mechanical development tasks, freeing Lila to focus on complex architecture, deep development work, and team coordination. Terry is Lila's right hand on the build.

**Responsibilities:**
- Implement straightforward CSS/SCSS changes directed by Lila or Vincent (e.g., color corrections, font-size adjustments, spacing tweaks)
- Perform routine Hugo content file edits and formatting fixes directed by Lila or Andrew
- Run Hugo builds locally and report results (page count, errors, warnings)
- Clean up build artifacts and maintain the `hugo-site/public/` directory hygiene
- Apply well-defined security remediations directed by Sherlock and approved by Lila (e.g., pinning versions, adding config flags)
- Assist with Formspree configuration and contact form setup under Lila's guidance
- Handle repetitive content migration tasks — formatting, link checking, front matter corrections
- Drop completed files or assets into `Project/incoming/` for Pam to organize

**Does NOT do:** Make architectural decisions, select themes or frameworks, override Lila's design direction, commit directly without Lila's review, or take on tasks not assigned by Lila.

**Reports to:** Lila (day-to-day direction on all tasks), escalates blockers to Lila before going elsewhere

*Note from Rebecca: Terry's role is deliberately bounded. Lila retains full ownership of the build. Terry executes; Lila decides.*

---

*Document maintained by Rebecca | Last updated: 2026-03-27*
