# PRD — Technical Architecture & Deployment
**Project:** Overlooked Heritage Map (working title: *Whose Heritage?*)
**Feature:** Production architecture, hosting, content pipeline, and deployment
**Parent documents:** Overlooked Heritage Map PRD · UI & Prototype PRD · Design Requirements PRD (July 2026)
**Status:** Decisions locked by project team, July 2026 — for confirmation with Rebecca at next meeting
 
---
 
## 1. Purpose
 
Lock in the technical decisions for the production website so the build can proceed immediately after the next meeting. The architecture is chosen against three hard constraints from the parent PRD: **~£10/year total running cost**, **near-zero maintenance** (students + one busy practitioner), and **non-technical editing** (Rebecca must be able to add and amend entries without a developer).
 
## 2. Locked Decisions
 
| Decision | Choice | Locked |
|---|---|---|
| Site type | Hand-built static site (single-page map app), evolved directly from the approved prototype | ✅ |
| Hosting | **GitHub Pages** (free) | ✅ |
| Domain | Custom domain (e.g. `.org.uk`/`.uk`), ~£10/year — the project's only running cost | ✅ |
| Content store / CMS | **Google Sheet**, published to web as CSV; site fetches it on page load | ✅ |
| Submissions | **Google Form** → "Queue" tab in the same Sheet; team reviews at biweekly meetings and promotes approved rows to the "Live" tab | ✅ |
| Photos | Uploaded to the GitHub repo via the web interface; filename referenced in the Sheet | ✅ |
| Map library | **Leaflet** + markercluster (as prototyped) | ✅ |
| Base map tiles | **CARTO light basemap** (free with attribution), greyscaled via CSS filter | ✅ |
| Frameworks / build step | **None.** Plain HTML/CSS/JS in one repo; no bundler, no dependencies to update | ✅ |
| Structural code changes | AI-assisted workflow (site is a single readable HTML file; paste → describe change → replace) | ✅ |
 
**Ruled out:** Cargo (public sites cost ~$14/month billed annually — roughly £130/year, 13× budget; embeds can't deliver the filtered colour-coded map; retained as aesthetic reference only) · Felt/uMap (loss of design system; free-tier risk) · WordPress/CMS platforms (ongoing update/security maintenance the team cannot absorb) · Netlify/Cloudflare Pages (equivalent to GitHub Pages; held as fallbacks, not needed).
 
## 3. Architecture Overview
 
```
                    ┌─────────────────────────────┐
                    │       GOOGLE SHEET          │
                    │  ┌──────────┐ ┌──────────┐  │
  Google Form ────► │  │  QUEUE   │ │   LIVE   │  │ ◄── Rebecca / team edit
  (public submits)  │  │  (tab 2) │ │  (tab 1) │  │     directly in browser
                    │  └──────────┘ └────┬─────┘  │
                    └────────────────────┼────────┘
                         team promotes   │  published as CSV (read-only)
                         rows at meeting │
                                         ▼
   GitHub repo ──────────────► GITHUB PAGES (free hosting)
   • index.html (map app)          │
   • /images (entry photos)        ▼
   • CNAME (custom domain)    whoseheritage.org.uk  ── visitor's browser
                                   │                    fetches CSV + tiles
                              CARTO tiles (free)        at page load
```
 
**Key property: the two halves are independent.** Content lives in the Sheet (exportable, portable, survives any platform change — protects the book/research ambition). Presentation lives in the repo (versioned, free to host anywhere). Either can be replaced without losing the other.
 
## 4. Content Pipeline (day-to-day)
 
1. **Add/edit an entry:** open the Google Sheet → edit the Live tab → save. The site reflects it on next page load. No deploy, no developer, no delay.
2. **Add a photo:** open the repo in a browser → `images/` → "Upload files" (drag & drop) → put the filename in the entry's row.
3. **Handle a submission:** Form responses appear in the Queue tab with a timestamp. At the biweekly meeting: research, fact-check, write the entry, cut the row into the Live tab (or mark rejected with a reason, kept for the record).
4. **Change the site itself** (new field, new page, layout change): AI-assisted edit of `index.html`, reviewed by whoever on the team is comfortable, committed via the GitHub web editor. Expected frequency: rare.
**Access control:** Sheet edit access = the editorial team only (Google account sharing). Repo write access = team GitHub accounts. The published CSV is read-only to the world. No login system is built or maintained — Google's and GitHub's permissions *are* the admin layer.
 
## 5. Sheet Schema (Live tab — locked to the agreed entry fields)
 
| Column | Format | Notes |
|---|---|---|
| `name` | text | Entry title |
| `lat`, `lng` | decimal | Pin position |
| `location` | text | Human-readable area/address |
| `tags` | comma-separated slugs | `wc, mig, lgbtq, wom, youth, health, care, soc`; first tag colours the dot |
| `description` | text | Rebecca's copy |
| `placetype` | text | Free text, e.g. `Community centre`, `Place of worship`; blank if none |
| `recognition` | text | Free text, e.g. `Grade II listed`; blank if none |
| `references` | semicolon-separated | Displayed as the sources list |
| `status` | `at risk` / `proposed for redevelopment` / `vacant` / `closed` / `demolished` | Controlled values |
| `photo` | filename | e.g. `bridge-park.jpg`; blank → standard placeholder |
| `published` | `yes` / `no` | Lets an entry be drafted in place without appearing |
 
Queue tab columns are set by the Google Form: timestamp, site name, location, submitter email (optional), plus team columns for `status` (new / researching / approved / rejected) and notes.
 
## 6. Deployment Plan (one-time setup, ~half a day)
 
1. Create project GitHub account/organisation; create public repo.
2. Add production `index.html` (prototype rewired to fetch the Sheet CSV) and `images/`.
3. Enable GitHub Pages on the repo (Settings → Pages → deploy from main branch).
4. Register domain (~£10/yr); add `CNAME` file + DNS records; enable HTTPS (automatic, free).
5. Create the Google Sheet from the template schema; File → Share → Publish to web → CSV; paste the CSV URL into `index.html`.
6. Create the Google Form; link responses to the Queue tab.
7. Seed 10–15 fact-checked launch entries over the summer (per parent PRD timeline).
8. Dry run: a non-technical team member adds a test entry end-to-end without help. **Launch is blocked until this passes.**
## 7. Costs
 
| Item | Cost |
|---|---|
| Hosting (GitHub Pages) | £0 |
| Content store (Google Sheets) | £0 |
| Submissions (Google Forms) | £0 |
| Map tiles (CARTO free tier, attributed) | £0 |
| Map library (Leaflet, open source) | £0 |
| Domain | **~£10/year** |
| **Total running cost** | **~£10/year** |
 
No component has a paid tier the project is quietly growing into; traffic on GitHub Pages and CARTO's free basemaps comfortably covers a project of this scale.
 
## 8. Risks & Mitigations
 
| Risk | Mitigation |
|---|---|
| Structural site changes need code | Content changes (95% of edits) never touch code; AI-assisted workflow for the rest; site is deliberately one readable file |
| Google retires Sheet "publish to web" or changes CSV format | Data is a plain spreadsheet — export and re-point the fetch at any CSV host; presentation layer unaffected |
| CARTO changes free-tier terms | Swap tile URL (one line) to OSM raster + CSS greyscale, or self-host Protomaps tiles in the repo |
| Team turnover / academic-year drift | Everything is browser-based and documented in §4; no local dev environment exists to lose; repo + Sheet ownership held by a shared project account, not an individual |
| Sheet edited badly (broken row) | `published` column gates visibility; site skips malformed rows rather than failing; Sheet has version history for rollback |
| GitHub Pages discontinued | Static files are portable in minutes to Cloudflare Pages/Netlify; domain simply re-points |
 
## 9. Success Criteria
 
- Site is live on the custom domain at ~£10/year total cost.
- Rebecca adds and edits an entry, unassisted, in under 5 minutes.
- A public submission travels Form → Queue → fact-check → Live without any code being touched.
- The full dataset exports to CSV in one click at any time.
- Nothing requires routine maintenance: no updates, patches, renewals (beyond the domain), or server administration.
## 10. Open Questions
 
1. **Domain name** — blocked on the project name decision (*Whose Heritage?* candidate); register as soon as the name locks.
2. **Account ownership** — create shared project Google + GitHub accounts (recommended) vs. using a team member's personal accounts?
3. **Analytics** — none by default (privacy-clean, zero-maintenance); is a lightweight privacy-respecting counter wanted for funding applications?
4. **Photo rights workflow** — feeds from the Design PRD's open question; the repo needs a `credits` convention once the process is agreed.
 