# PRD — Website UI & Clickable Prototype
**Project:** Overlooked Heritage Map (working title: *Whose Heritage?*)
**Feature:** v1 user interface + clickable HTML prototype
**Parent document:** Overlooked Heritage Map PRD (July 2026)
**Status:** Draft — decisions below confirmed with project team; visual details pending Rebecca's review
 
---
 
## 1. Purpose
 
Produce a clickable HTML prototype of the public website UI, good enough to present at the next project meeting and to give Rebecca a concrete artefact to react to on narrative, wording, and layout. The prototype is a design tool, not production code — but it should be close enough to the real thing that decisions made against it carry through to the build.
 
## 2. Confirmed UX Decisions
 
| Decision | Choice |
|---|---|
| Landing experience | **Full-screen map immediately** — the map *is* the homepage; no intro page before it |
| Opening an entry | **Side panel** slides in next to the map when a pin is clicked; map stays visible and repositions/pans so the selected pin isn't hidden |
| Tag filtering | **Always-visible filter bar** overlaid on the map |
| Pin style | **Dots, colour-coded by tag** |
| Navigation (About / Research / Submit) | **Hamburger menu — open by default on first load, collapsible** by the user |
| Deliverable | **Clickable HTML prototype** (single self-contained file, works in any browser) |
 
## 3. Screen-by-Screen Requirements
 
### 3.1 Map view (home)
- Full-viewport map of the UK, muted **greyscale base map** (urban/rural contrast legible — the grey aesthetic from the My Atlas mock-up).
- Colour-coded dots for entries. Colours are the *only* saturated elements on the page; everything else stays black/white/grey so the data carries the visual weight.
- Dot legend integrated into the filter bar (colour = tag, so filter and legend are the same component — no duplication).
- Site name/wordmark small and fixed in a corner; geometric, black on white.
- Hover on a dot (desktop): tooltip with entry name. Click/tap: opens side panel.
- Clustering behaviour when zoomed out (e.g. numbered cluster circles around Manchester/Birmingham) so dense urban areas stay readable.
### 3.2 Hamburger navigation
- **Open on first load** so first-time visitors immediately see what the site is; collapsible via the hamburger icon and auto-collapses when the user interacts with the map.
- Contains: **About** (incl. Bridge Park origin story), **Research / References**, **Submit a site**, **Contact**.
- When open, renders as a slim left column over the map — not a full-page takeover.
- One or two sentences of project mission at the top of the open menu, so the "what is this?" question is answered without leaving the map.
### 3.3 Filter bar
- Always visible, overlaid on the map (bottom or top edge — prototype should test bottom first).
- One toggle chip per tag: *Working-class · Industrial · Diaspora · Traveller* (+ room for future tags).
- Each chip shows its tag colour (doubles as the legend). Toggling a chip shows/hides those dots instantly.
- "All" state is default; active filters visually obvious; one-tap reset.
### 3.4 Entry side panel
- Slides in from the right (~35–40% of viewport on desktop); map remains interactive.
- Content order: photograph → entry name → tag chips → location → description → references/sources → status (extant / at risk / demolished).
- Close via ✕, clicking the map, or Esc.
- Panel is scrollable for longer entries; typography-led, generous white space, geometric rules/dividers — consistent with the Save Bridge Park / Cargo design sensibility.
### 3.5 Static pages (About, Research, Submit)
- Open as simple overlay pages or panels from the hamburger — visitor never feels they've "left" the map site.
- Text-led, minimal, black-and-white. Submit page = short explanation + email address / simple form (name of site + location is all we ask for; the team does the rest).
## 4. Mobile Behaviour
 
- Map remains the landing view; hamburger starts **collapsed** on mobile (screen space is scarce) with the mission sentence shown once as a dismissible banner instead.
- Side panel becomes a **bottom sheet**: peek state (photo + title) on tap, drag up for full entry.
- Filter bar collapses to a single "Filter" chip that expands the tag list.
- All touch targets ≥ 44px.
## 5. Visual Language
 
- Black-and-white, clear, geometric, generous white space; "design-world" restraint (Cargo-adjacent) but never at the cost of legibility for a first-time, non-professional visitor.
- Greyscale map; tag colours are the sole accent palette — pick colours that remain distinguishable for colour-blind users and print (relevant to the future book).
- Typography: one strong grotesque/sans for everything; hierarchy through size and weight, not decoration.
- No stock imagery, no gradients, no drop shadows beyond what's needed for panel separation.
## 6. Prototype Scope
 
**In scope**
- Single self-contained HTML file, openable in any browser, shareable by email/link.
- Working map interactions: pan/zoom, ~10–15 sample entries with placeholder content, colour-coded dots, working filters, working side panel, hamburger open/collapse, and stub About/Research/Submit pages.
- Desktop-first, with the mobile bottom-sheet pattern demonstrated if feasible.
**Out of scope (prototype)**
- Real data entry/admin flows, real submissions handling, CMS integration, accounts.
- Final copy — all text placeholder, clearly marked, since wording is Rebecca's domain.
- Final tag colour choices — prototype proposes a palette for reaction, not sign-off.
## 7. Success Criteria
 
- A first-time viewer understands the project within 30 seconds of the prototype loading (open hamburger + map should achieve this together).
- Rebecca can react to layout and structure concretely ("move this, reword that") rather than in the abstract.
- Every confirmed decision in §2 is demonstrable by clicking, not described in words.
- Ready to present at the meeting in ~2 weeks.
## 8. Open Questions
 
1. Tag colour palette — how many tags do we expect long-term, and do colours need to work in print for the book?
2. Filter bar position — bottom vs top edge (prototype to test bottom first).
3. Should the side panel link out to a full standalone entry page later (for sharing/citing individual entries), or is the panel the entry's permanent home?
4. Does the greyscale base map come from the chosen mapping tool's styling options, or do we constrain the tool choice to whatever supports it? (Feeds back into the parent PRD's mapping-tool question.)
 