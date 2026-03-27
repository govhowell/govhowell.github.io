# Structure & Design Audit — Governor Howell Website
**Owner:** Lila (Chief Web Designer & Architect)
**Status:** IN PROGRESS
**Started:** 2026-03-26

> Document the current site's information architecture, identify structural problems, and propose the new Hugo site structure.

---

## Current Site Map (WordPress Export)

```
govhowell.org/
├── index.html
├── blog/
├── timelines/
│   ├── revolutionary-war-timeline/
│   ├── pre-war-timeline/
│   └── post-war-timeline/
├── letters/
│   ├── pre-war-letters/
│   ├── post-war-letters/
│   ├── revolutionary-war-correspondence/
│   ├── letter-from-richard-howell-to-col-israel-shreve-5-oct-1778/
│   └── rh-writes-arnold1/
├── people/
│   ├── dr-lewis-howell/
│   ├── varina-howell-davis/
│   └── william-howell-1793-1863/
├── history/
│   ├── 2nd-new-jersey-regiment/
│   ├── greenwich-tea-burning/
│   └── howell-family-history/
├── resources/
│   ├── family-tree/
│   ├── maps/
│   ├── homestead/
│   └── documents/
├── contact-us/
├── new-web-page-design/       ← previous redesign attempt
├── wp-content/uploads/        ← 806 media files
├── wp-content/themes/         ← discard
├── wp-includes/               ← discard
└── wp-json/                   ← discard
```

---

## Structural Problems Identified

*(Lila fills in as audit progresses)*

-

---

## Proposed Hugo Site Structure

*(Draft — to be refined in coordination with Andrew)*

```
hugo-site/
├── content/
│   ├── _index.md              ← Homepage
│   ├── biography/
│   ├── timelines/
│   ├── letters/
│   ├── people/
│   ├── events/
│   ├── family/
│   └── resources/
├── static/
│   ├── images/
│   ├── documents/
│   └── maps/
├── themes/
├── layouts/
├── data/
└── hugo.toml
```

---

## Content Type Definitions (Hugo)

*(Define the front matter schema for each content type)*

### Person
```yaml
---
title:
born:
died:
role:
relation_to_richard_howell:
summary:
---
```

### Letter
```yaml
---
title:
date:
from:
to:
repository:
transcription_notes:
---
```

### Timeline Entry
```yaml
---
title:
date:
period: [pre-war | revolutionary-war | post-war]
location:
summary:
---
```

### Historical Event
```yaml
---
title:
date:
location:
participants:
significance:
---
```

---

## Theme Options

*(Research and present 3 options to Richard — due 2026-04-02)*

| # | Theme Name | URL | Pros | Cons | Rating |
|---|-----------|-----|------|------|--------|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |

**Recommendation:**

---

## `new-web-page-design/` Assessment

*(Review this folder — is anything worth salvaging?)*

-

---

*Document owner: Lila | Created: 2026-03-26*
