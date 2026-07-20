# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**This Place Counts** (working title: *Whose Heritage?*) is an interactive map documenting overlooked heritage across the UK — working-class, diaspora, industrial, and Traveller community heritage that the formal heritage system ignores. Led by Rebecca (heritage lead with editorial control) and a team of architecture students.

The project serves two audiences simultaneously: heritage professionals (English Heritage, researchers) and everyday community members who may never have engaged with heritage before. Every entry is fact-checked and referenced; nothing goes live without editorial approval.

## Architecture

**Zero-framework static site.** One self-contained HTML file (`index.html`) with inline CSS and JS. No bundler, no build step, no dependencies to install or update.

- **Map:** Leaflet + MarkerCluster, CARTO light basemap greyscaled via CSS `filter: grayscale(1)`
- **Content store:** Google Sheet published as CSV, fetched client-side on page load. The site never touches the Sheet — it's read-only
- **Submissions:** Google Form → Queue tab in the Sheet → team fact-checks → promotes to Live tab
- **Photos:** Stored in `images/` directory; filename referenced in the Sheet row
- **Hosting:** GitHub Pages (free), custom `.org.uk` domain (~£10/year — the only cost)

Content changes (95%+ of edits) happen in the Google Sheet and require zero code changes.

## Current State

The `260718_docs/` folder contains the PRD pack and a clickable HTML prototype:

- `overlooked-heritage-prd.md` — master PRD (goals, users, features, constraints)
- `heritage-tech-architecture-prd.md` — hosting, content pipeline, Sheet schema, deployment plan
- `heritage-design-requirements-prd.md` — full design system and visual identity rules
- `heritage-ui-prototype-prd.md` — UI decisions and prototype scope
- `heritage-setup-accounts-prd.md` — account ownership, access model, onboarding/offboarding
- `this-place-counts-prototype (1).html` — working clickable prototype (644 lines, single file)

The prototype has hardcoded sample entries; production will fetch from the published Google Sheet CSV.

## Design System (strict rules)

These are non-negotiable — Rebecca has final sign-off on all visual decisions.

**Colour:** The interface is achromatic (`#111` ink, `#6B6B6B` grey, `#E2E2E2` hairline, `#FFF` paper). Saturated colour appears **only** on data (tag-coded dots/chips). If it's coloured, it's data. No coloured buttons, links, or decorations.

**Tag palette** (Okabe-Ito, colour-blind safe):
| Tag | Slug | Hex |
|---|---|---|
| Working-class heritage | `wc` | `#E69F00` |
| Migrant and diasporic heritage | `mig` | `#0072B2` |
| LGBTQ+ heritage | `lgbtq` | `#CC79A7` |
| Women's history | `wom` | `#D55E00` |
| Youth culture | `youth` | `#56B4E9` |
| Health and wellbeing | `health` | `#009E73` |
| Community care | `care` | `#F0E442` |
| Social movements | `soc` | `#AA4499` |

**Typography:** Space Grotesk only. Hierarchy via size and weight — no italic for emphasis, no colour for emphasis. Uppercase + letterspacing for labels. Reading text: 15px min, 1.6 line height, max ~52ch.

**Geometry:** Zero border-radius everywhere (except map dots, which are round because they're data). No shadows, no gradients, no blurs. 1px rules for structure. 8px baseline grid, padding steps: 12/16/24/32/40.

**Imagery:** Documentary photography only. No stock, no illustration, no AI-generated images. Missing photos get the grey hatch placeholder.

**Motion:** Functional only (300-350ms slide, strong ease-out). `prefers-reduced-motion` respected. Nothing animates on its own.

**Accessibility floor:** WCAG AA contrast, 44px touch targets, visible keyboard focus (2px ink outline), fully usable in greyscale.

## Sheet Schema (Live tab)

| Column | Format |
|---|---|
| `name` | text |
| `lat`, `lng` | decimal |
| `location` | text (human-readable) |
| `tags` | comma-separated slugs: `wc`, `mig`, `lgbtq`, `wom`, `youth`, `health`, `care`, `soc` |
| `description` | text |
| `references` | semicolon-separated |
| `status` | `extant` / `at risk` / `demolished` |
| `photo` | filename (e.g. `bridge-park.jpg`) |
| `published` | `yes` / `no` |

## Key Constraints

- **Budget:** ~£10/year total. Everything must be free-tier
- **No build step:** Plain HTML/CSS/JS. No npm, no bundler, no framework
- **Non-technical editors:** Rebecca must add/edit entries in the Google Sheet without developer help
- **Single HTML file:** The site is deliberately one readable file for AI-assisted editing
- **Editorial control:** All content wording is Rebecca's domain. Placeholder copy is marked with `⟨angle brackets⟩` and italic
- **Data ownership:** The Sheet is the canonical dataset, independent of the presentation layer, exportable at any time (protects long-term book/research ambitions)
