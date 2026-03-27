# Hugo Theme Options — Governor Howell Website
**Owner:** Lila (Chief Web Designer & Architect)
**Status:** READY FOR DECISION
**Presented:** 2026-03-26

---

## Evaluation Criteria

| Criterion | Weight | Notes |
|-----------|--------|-------|
| Historical/scholarly aesthetic | High | Site is an archival resource |
| Multi-section navigation | High | Timelines, letters, bios, events all need distinct layouts |
| Long-form readability | High | Primary source letters, narrative history |
| Mobile responsive | Required | |
| GitHub Pages compatible | Required | |
| Active maintenance | Medium | Want long-term support |
| Print support | Medium | Researchers may want to print letters |
| Minimal JS | Medium | Keep it fast and simple |

---

## Option 1 — Hugo Book

**GitHub:** https://github.com/alex-shpak/hugo-book
**Demo:** https://hugo-book-demo.netlify.app
**License:** MIT
**Stars:** ~3,980 | **Last commit:** March 2026 (actively maintained)

**Style:** Clean, spare, documentation-style. Persistent left-sidebar tree-navigation. Wide content column. Reads like a well-set reference book. Light/dark mode.

**Pros for this project:**
- Persistent hierarchical sidebar — ideal for Biography > Timelines > Letters > Events navigation
- Built-in per-page table of contents (critical for long letter transcriptions)
- Zero JS framework dependency — pure static, GitHub Pages compatible
- In-page search via FlexSearch (no external service)
- Most actively maintained theme of the three
- Shortcodes for hints, callout boxes, expandable details — useful for citation notes and transcription notes
- MIT license

**Cons:**
- Default aesthetic reads as modern software docs — will need custom CSS for serif font and warmer palette
- Taxonomy browsing (letters by correspondent, events by year) requires extra configuration
- Sidebar assumes single-root doc tree; multi-section Hugo architecture needs config planning

**Rating: 8.5 / 10**

---

## Option 2 — Mainroad

**GitHub:** https://github.com/Vimux/Mainroad
**Demo:** https://mainroad-demo.netlify.app
**License:** GPLv2
**Stars:** ~1,044 | **Last commit:** September 2024 (stable, slower cadence)

**Style:** Two-column journal/magazine layout. Content on left, configurable widget sidebar on right. Feels like a serious online periodical or reference journal. Clean, typographically sound.

**Pros for this project:**
- Journal aesthetic is the closest to "right out of the box" for a scholarly history site — minimal customization needed
- Native taxonomy support — Categories and Tags with full index pages; enables "Browse letters by correspondent" with no custom work
- Widget sidebar is independently configurable per page type (home, list, single)
- Multiple menu positions (main, side, footer)

**Cons:**
- No persistent tree-navigation sidebar — readers can't see section structure at a glance
- GPLv2 license (not MIT — not a problem for this site, but worth knowing)
- Last feature commit September 2024 — stable but not growing
- Long letter transcriptions get standard article layout — no specialized document view
- Sidebar shows site-wide tags/recent articles, not section-scoped navigation

**Rating: 7.5 / 10**

---

## Option 3 — Hugo Relearn

**GitHub:** https://github.com/McShelby/hugo-theme-relearn
**Demo:** https://mcshelby.github.io/hugo-theme-relearn/
**License:** MIT
**Stars:** ~588 | **Last commit:** March 2026 (very actively maintained)

**Style:** Full-width documentation environment with persistent collapsible left sidebar, topbar, and wide content area. Multiple built-in color palettes. Reads as a modern knowledge base — most customization needed to achieve historical aesthetic.

**Pros for this project:**
- Most feature-complete of the three: hierarchical sidebar, breadcrumbs, in-page search (three modes), child-page listing, versioning
- **Native print support** — entire site or individual sections can be printed as a coherent document. Valuable for a primary-source letter archive where researchers want to print letters.
- 15+ shortcodes: tabs (original text vs. transcription), expandable sections, notice/hint boxes, lightbox image support with sizing — all useful for primary source document presentation
- Image shortcodes support lightbox display of historical document scans alongside transcriptions
- 25+ language translations; very active development with proper versioning and changelog
- MIT license

**Cons:**
- Most JS of the three (though most is optional/toggleable) — slightly heavier
- Default aesthetic is the furthest from historical — requires more deliberate CSS customization
- Smaller community (~588 stars) — fewer tutorials and third-party resources
- Single-root sidebar assumption requires configuration planning for multi-section architecture

**Rating: 7.5 / 10**

---

## Comparison Summary

| Criteria | Option 1: Book | Option 2: Mainroad | Option 3: Relearn |
|----------|---------------|-------------------|-------------------|
| License | MIT | GPLv2 | MIT |
| Stars | 3,980 | 1,044 | 588 |
| Maintenance | Active (Mar 2026) | Stable (Sep 2024) | Very Active (Mar 2026) |
| Tree-nav sidebar | Yes | No | Yes |
| Taxonomy browsing | Minimal | Strong | Moderate |
| **Print support** | **No** | **No** | **Yes** |
| JS weight | Minimal | Minimal | Moderate (optional) |
| Default aesthetic | Clean/modern doc | Journal/magazine | Modern wiki |
| CSS customization needed | Low | Minimal | Moderate |
| **Rating** | **8.5/10** | **7.5/10** | **7.5/10** |

---

## Lila's Recommendation

**Option 1 (Hugo Book)** is the strongest structural fit — the tree-sidebar navigation is exactly right for this content architecture, and it's the most actively maintained.

**However:** If print support for researchers (printing letter transcriptions, printing timeline sections) is something the site should support, **Option 3 (Relearn)** moves to the top. It's the only one of the three with native print output. The extra customization cost is real but manageable.

**Option 2 (Mainroad)** is the right call only if Richard wants the most "historically appropriate" look with zero CSS work.

---

## Richard's Decision

**Selected Theme:** Option 1 — Hugo Book
**Date decided:** 2026-03-26
**Notes:** Richard selected Book for its navigation structure and clean foundation. Lila will build a custom parchment CSS skin on top — aged paper aesthetic, period serif typography. The historical look comes from the skin, not the base theme.

---

*Document owner: Lila | Completed: 2026-03-26*
