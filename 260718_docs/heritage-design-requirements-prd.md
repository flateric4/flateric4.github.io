# PRD — Design Requirements & Visual Identity
**Project:** Overlooked Heritage Map (working title: *Whose Heritage?*)
**Feature:** Design system governing all project outputs — website, prototype, and future print
**Parent documents:** Overlooked Heritage Map PRD · UI & Clickable Prototype PRD (July 2026)
**Status:** Draft — for Rebecca's sign-off; she holds final say on all visual decisions
 
---
 
## 1. Purpose
 
Define the visual rules for the project so that every output — the website, the prototype, presentation decks, and eventually the book — looks like it comes from one hand. The audience for this document is the project team (architects doing the graphic work) and any future collaborator or AI tool asked to produce material for the project.
 
## 2. Design Position
 
The team are architects; the design should read as such. The reference points are **Cargo-hosted studio sites, the Save Bridge Park site, and print-led editorial design** — not tech-product design. The site should feel closer to a well-set exhibition catalogue than to a startup landing page.
 
But there is a tension to hold deliberately: the same design must work for **an English Heritage panel and an 80-year-old Windrush-generation woman who has never used a heritage website**. Minimalism here is a legibility strategy, not a style flex. Every reduction must make the content clearer; any reduction that makes the site harder for a first-time, non-professional visitor is wrong, however good it looks.
 
**Governing principle: the archive is the design.** The interface recedes; the entries, the map, and the pattern they form carry all the visual weight.
 
## 3. Colour
 
### 3.1 Base palette (the interface)
The interface is achromatic. No tints, no brand colour.
 
| Token | Hex | Use |
|---|---|---|
| Ink | `#111111` | All text, borders, active states |
| Grey | `#6B6B6B` | Secondary text, labels, placeholder copy |
| Hairline | `#E2E2E2` | Dividers, inactive borders |
| Paper | `#FFFFFF` | All backgrounds |
 
### 3.2 Tag palette (the data)
Tag colours are the **only saturated elements anywhere in the project**. If something is coloured, it is data; if it is data, it is coloured. This rule is absolute — no coloured buttons, links, highlights, or decorations.
 
Proposed palette (Okabe–Ito set — colour-blind safe, distinguishable in CMYK print for the book):
 
| Tag | Slug | Hex | |
|---|---|---|---|
| Working-class heritage | `wc` | `#E69F00` | orange |
| Migrant and diasporic heritage | `mig` | `#0072B2` | blue |
| LGBTQ+ heritage | `lgbtq` | `#CC79A7` | pink |
| Women's history | `wom` | `#D55E00` | vermillion |
| Youth culture | `youth` | `#56B4E9` | sky blue |
| Health and wellbeing | `health` | `#009E73` | green |
| Community care | `care` | `#F0E442` | yellow |
| Social movements | `soc` | `#AA4499` | purple |

All eight colours are drawn from the Okabe–Ito set (plus one Paul Tol addition for colour-blind safety). Where an entry has multiple tags, the **first (primary) tag** colours its dot; all tags appear as chips in the entry panel. The filter bar displays all eight tags in a 4×2 grid layout.
 
### 3.3 Map
Base map is fully greyscale (desaturated at source or via filter). Urban/rural contrast must remain legible at national zoom — the grey field is what makes the coloured dots, and therefore the pattern, readable.
 
## 4. Typography
 
- **One typeface for everything:** a geometric grotesque. Prototype uses **Space Grotesk**; acceptable alternatives if licensing/hosting demands: Archivo, Neue Haas Grotesk, Helvetica Now. One family, never mixed.
- **Hierarchy through size and weight only.** No italic for emphasis (italic is reserved for marking placeholder copy in drafts), no underlines except link hover, no colour for emphasis.
- Type scale (web): 34 / 26 / 20 / 15 / 12 / 10 / 9 px. Nothing in between.
- **Uppercase + letterspacing (0.12–0.22em) is the project's label voice** — used for field names, statuses, filters, and wayfinding. Sentence case for all reading text.
- Reading text: 15px minimum, 1.6 line height, max measure ~52 characters. Legibility for older and non-professional readers overrides density.
## 5. Space, Line & Geometry
 
- **Generous white space is a feature, not a gap to fill.** When in doubt, remove an element rather than shrink the spacing.
- **Zero border-radius everywhere.** Right angles only — panels, buttons, inputs, images. The sole exceptions are the map dots and cluster circles, which are round *because they are data points*.
- Rules and hairlines do the structural work: 1px Ink for primary divisions (panel edges), 1px Hairline for secondary (field dividers). Never boxes within boxes.
- No drop shadows, no gradients, no blurs. Panel separation is achieved by a 1px Ink border alone. (One tolerated exception: the subtle halo on map dots needed to lift them off the grey map.)
- Layout aligns to an 8px baseline; padding steps of 12 / 16 / 24 / 32 / 40.
## 6. Imagery
 
- **Documentary photography only.** Entry photographs are records, not decoration — no stock imagery, no illustration, no AI-generated images, ever.
- Photographs are presented as-shot: no filters, no duotones, no colour grading. (Full-colour photography is welcome inside entries — the "colour = data" rule applies to interface elements, and a photograph is content.)
- Missing photographs get the standard placeholder: grey field, diagonal hatch, "PHOTOGRAPH — TBC". Never a stand-in image.
- Aspect ratio 4:3 in the entry panel; crops respect the building/site, not the composition trend.
## 7. Iconography & Ornament
 
- Near-zero icon set: hamburger (three lines), close (✕), and the map dots themselves. Nothing else. Where an icon might be used, use a word instead — words are clearer for the non-professional audience.
- No decorative ornament of any kind. If an element does not encode information, it is removed.
## 8. Motion
 
- Motion is functional wayfinding only: panels slide (300–350ms, strong ease-out), map transitions use smooth fly-in animations (1.2s duration) for pin clicks, cluster clicks, and sites list navigation. Filter changes are instant.
- Nothing animates on its own. No parallax, no scroll effects, no hover flourishes beyond a link's underline or indent.
- `prefers-reduced-motion` is respected: all transitions collapse to instant.
## 9. Accessibility Floor (non-negotiable)
 
- Text contrast ≥ WCAG AA on all sizes (Ink and Grey on Paper both pass).
- Tag colours are never the sole carrier of meaning — every tag also appears as a written label.
- Touch targets ≥ 44px; visible keyboard focus (2px Ink outline) on everything interactive.
- The site must remain fully usable in greyscale (relevant both to colour-blind users and to black-and-white print of the future book).
## 10. Print Continuity (the book)
 
Design decisions made now should survive translation to print in several years:
- The tag palette must hold in CMYK and remain distinguishable in a printed key (Okabe–Ito does).
- The typographic system (one grotesque, uppercase label voice, hairline rules) is directly reusable as the book's typesetting.
- Entry field structure (name → tags → location → place type → existing recognition → description → references → status) is the future page template.
## 11. Do / Don't Summary
 
| Do | Don't |
|---|---|
| One typeface, black on white | Mixed faces, tinted backgrounds |
| Colour only on data | Coloured UI, brand accent colours |
| 1px rules for structure | Shadows, cards, rounded corners |
| Words over icons | Icon sets, decorative symbols |
| Documentary photographs | Stock, illustration, AI imagery |
| Remove before you shrink | Fill white space |
 
## 12. Governance
 
- **Rebecca signs off** all visual decisions, wording, and any departure from this document. The subject matter is contested; visual tone is part of editorial control.
- This document is versioned alongside the other PRDs; changes are agreed at the biweekly meeting, not made ad hoc.
- Any tool, template, or collaborator producing project material is given this document first.
## 13. Open Questions
 
1. Final typeface licensing — Space Grotesk is free (OFL); confirm it satisfies the "design-world" bar, or budget for Neue Haas Grotesk.
2. Does the wordmark stay purely typographic, or is a minimal mark (e.g. a single dot) permitted? (Recommend: typographic only.)
3. Photography sourcing and rights process for entries — who shoots, who clears archive images, and how are credits displayed?
4. Tag colour sign-off — palette above is proposed for reaction, pending Rebecca's review against the first real entries.
 