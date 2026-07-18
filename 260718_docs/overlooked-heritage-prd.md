# Product Requirements Document — Overlooked Heritage Map
**Working title:** TBC (candidate: *Whose Heritage?*, after the 1990s essay)
**Status:** First draft, for review at next project meeting
**Owner:** Rebecca (heritage lead / editorial control), supported by project team (architects: graphics, opinion, build)
**Date:** July 2026
 
---
 
## 1. Background & Problem Statement
 
The UK heritage system disproportionately recognises and protects a narrow band of heritage (e.g. Victorian buildings), while the heritage of working-class communities, diaspora communities, the Traveller community (whose heritage is movable and rarely fits statutory designation), and industrial sites is systematically overlooked. There is currently no accessible, well-maintained platform that documents this overlooked heritage in one place.
 
This project grew out of the **Bridge Park project** and asks: *whose heritage is being overlooked, and does the current heritage system reasonably protect our heritage — or is it an echo chamber?*
 
We are deliberately **not jumping to conclusions**. The purpose at this stage is to collect, archive, and arrange records on an accessible platform so that patterns can emerge and be analysed later.
 
## 2. Goals
 
1. **Archive** overlooked heritage sites/projects in a structured, consistent database.
2. **Map** entries visually so geographic patterns (e.g. clustering around urban centres like Manchester and Birmingham) become visible.
3. **Tag** entries by theme (e.g. working-class heritage, diaspora community heritage, industrial heritage, Traveller heritage) so common themes can be surfaced.
4. **Reach two audiences at once:** heritage professionals (English Heritage, practitioners, researchers) *and* everyday people who have never engaged with heritage before — including the disconnected communities whose heritage the project documents.
5. **Enable future outputs:** long-term (years), the dataset should support analysis and potentially a published book.
### Non-goals (for v1)
- Public self-service uploading (no open wiki model).
- Complex CMS, user accounts for the public, or heavy interactive features.
- Duplicating heritage that is already formally recognised. Every entry must genuinely align with the "overlooked heritage" premise — no doubling up on existing records.
## 3. Users
 
| User | Need |
|---|---|
| General public / local communities | Simple, jargon-free browsing; "I recognise that place" moments; ability to suggest a site |
| Community elders & disconnected communities | Accessible online platform; recognition of heritage the system ignores |
| Heritage professionals & researchers | Credible, referenced, fact-checked records; visible patterns for advocacy and policy discussion |
| Project team (editors) | Easy way to add/edit/approve entries without technical expertise; Rebecca needs direct editorial control over wording and layout |
 
## 4. Core Features (v1)
 
### 4.1 Interactive map (primary interface)
- Map of the UK with pins for each entry.
- Muted/grey base map aesthetic (urban vs rural contrast legible; reference: the My Atlas / Google My Maps mock-up already tested).
- Clicking a pin opens a summary with photo, short description, and link to a fuller entry.
### 4.2 Entry pages / records
Each record has consistent fields (already broadly agreed):
- Name of site/project
- Location (map coordinates + address/area)
- Photograph(s)
- Description / narrative
- Heritage tags (see 4.3)
- References / sources (essential for credibility)
- Status (e.g. extant, at risk, demolished)
### 4.3 Tagging system
- Controlled tag list, e.g. *working-class heritage, diaspora community heritage, industrial heritage, Traveller heritage*.
- Tags filterable on the map so themes and patterns can be explored.
### 4.4 Static pages (simple tab structure)
- **About** — the project, and the Bridge Park story that spurred it.
- **Research / References** — methodology and sourcing, for academic credibility.
- **Submit** — how the public can suggest a site (see 4.5).
- Possibly **Contact**.
### 4.5 Submissions workflow
- **v1 (simplest):** a public email address / contact form. Submitters only need to provide the name/location of a site; the team researches, fact-checks, and writes the entry.
- **v2 (nice-to-have):** lightweight admin login where an editor can review and approve queued submissions before they appear on the map.
- All content is moderated — nothing goes live without team fact-checking, because the subject area is contested and credibility is central.
## 5. Design Requirements
 
- **Simple and digestible above all.** Must work for someone who has never thought about heritage before.
- Clear, geometric, generous white space; black-and-white / restrained palette (reference: the existing Save Bridge Park site, Cargo-style design sensibility).
- Professional presentation — the site must hold up in front of English Heritage as well as a community meeting.
- Mobile-friendly (many community users will be on phones).
- Rebecca to have final say on wording, narrative, and layout; the build must make her edits easy (ideally editable directly in a browser, not locked in code).
## 6. Technical Requirements & Constraints
 
- **Budget:** ~£10/year currently available (domain-level budget). Free or near-free hosting strongly preferred; small funding may be pursued for hosting costs.
- **Maintenance:** must be robust and low-maintenance. The team is students + a busy practitioner; no one can continually refine or debug it. Prefer boring, reliable tools over clever ones.
- **Editability:** non-technical editors must be able to add and amend entries without a developer. (Risk identified: a fully hand-built site makes content changes harder; mitigate by using a platform/CMS or an AI-assisted editing workflow.)
- **Mapping tool:** *open question* — evaluate free/open-source options (e.g. Google My Maps embed as tested, Leaflet + OpenStreetMap, uMap, Felt). Criteria: free, embeddable, custom grey styling, supports tags/filters, exportable data.
- **Hosting:** *open question* — evaluate Cargo (team familiarity via Save Bridge Park), plus free options (e.g. GitHub Pages for a static build, or a low-cost site builder). Criteria: cost, ease of editing for Rebecca, map embedding, longevity.
- **Data ownership:** the underlying dataset (entries + fields) should live somewhere exportable (e.g. a spreadsheet or open format), independent of whichever platform renders it — this protects the long-term research and book ambitions.
## 7. Content & Editorial Principles
 
- Every entry must be researched and referenced; the site's authority depends on fact-checking.
- Entries must genuinely be *overlooked* — not restatements of already-designated heritage.
- Tone: accessible, non-academic on the surface; rigour in the references underneath.
- Sensitivity: this is a contested area; narrative and wording are controlled by the heritage lead.
## 8. Timeline & Ways of Working
 
| Milestone | Target |
|---|---|
| Draft concept (structure, look, sample entries) ready to present | Next meeting (~2 weeks) |
| Decide mapping tool + hosting platform | Within 2–4 weeks |
| Populate initial seed entries (fact-checked) | Over summer |
| Public v1 launch of website | End of summer |
| Ongoing: biweekly project meetings | Continuous |
| Long-term: pattern analysis, publicity, potential book | Years out |
 
## 9. Success Criteria
 
- v1 site live within the summer, at effectively zero running cost.
- Non-technical editors can add/approve an entry without developer help.
- A first-time visitor understands the project's purpose within 30 seconds.
- The map surfaces at least one visible pattern worth discussing (e.g. urban clustering).
- The site is credible enough to present to both a community audience and heritage bodies.
## 10. Open Questions
 
1. **Mapping tool** — which free tool best balances aesthetics, filtering/tags, and zero maintenance?
2. **Hosting** — Cargo vs free static hosting vs other builders; what does the £10/year realistically cover?
3. **Name** — still undecided (*Whose Heritage?* candidate).
4. **Submission handling** — start with email only, or build the lightweight admin/approval flow from day one?
5. **Governance** — who maintains the site and reviews submissions through the academic year, when everyone is busy?
6. **Funding** — which connections/grants to pursue for minimal hosting/running costs?
 