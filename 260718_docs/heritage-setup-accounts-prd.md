# PRD — Setup Requirements: Accounts, Access & Ownership
**Project:** Overlooked Heritage Map (working title: *Whose Heritage?*)
**Feature:** One-time project setup — the accounts, credentials, and access structure everything else runs on
**Parent documents:** Overlooked Heritage Map PRD · Technical Architecture PRD (July 2026)
**Status:** Draft — resolves Architecture PRD open question §10.2 (account ownership); for confirmation at next meeting
 
---
 
## 1. Purpose
 
Define what must be set up, by whom, and who holds the keys — before the production build begins. The architecture (GitHub Pages + Google Sheet) requires no servers and no logins to *build*, but it does depend on a small set of accounts. This document exists because the biggest long-term risk to a student-run, years-long project is not technical failure but **losing access**: a graduated team member's personal account quietly owning the whole archive.
 
**Governing principle: the project owns its accounts; people are granted access to them.** No critical asset lives under an individual's personal identity.
 
## 2. The Project Identity
 
One shared project email address is created first and owns everything downstream.
 
| Item | Choice |
|---|---|
| Project email | Free Gmail account, e.g. `whoseheritage.project@gmail.com` (adjust when the name locks) |
| Owns | GitHub account · Google Sheet & Form · domain registration · any future accounts (analytics, funding portals) |
| Password custody | Stored in a place the whole team can reach (see §6) |
| Recovery | Recovery email/phone set to **two different team members**, updated at handover (§7) |
 
Why Gmail: the Sheet and Form are Google-native, so the project email doubles as the Google account that owns the content store. One identity, everything attached to it.
 
## 3. Accounts to Create (in order)
 
| # | Account | Details | Cost |
|---|---|---|---|
| 1 | **Project email** (Gmail) | Per §2. Created before anything else | £0 |
| 2 | **GitHub** (project account) | Username = site URL until custom domain (e.g. `whoseheritage` → `whoseheritage.github.io`); Free plan; **2FA mandatory** — authenticator app + recovery codes saved to team storage | £0 |
| 3 | **Google Sheet + Form** | Created under the project Gmail; Sheet = content store (Architecture PRD §5 schema); Form = submissions → Queue tab | £0 |
| 4 | **Domain registrar** | Registered under the project email; UK registrar; `.org.uk`/`.uk` ~£10/yr. **Blocked on the name decision** | ~£10/yr |
| 5 | **Team members' personal GitHub accounts** | Free; needed to be added as collaborators and to generate upload tokens (Architecture PRD Appendix A) | £0 |
 
Explicitly **not** created: no hosting account beyond GitHub, no CMS, no analytics (pending Architecture PRD §10.3), no social accounts (out of scope here).
 
## 4. Repository Setup
 
1. Repo name: **`<username>.github.io`** — the special name that serves at the root URL.
2. Visibility: **Public** (required for free Pages; also fits the project's open ethos — the code and photos are public, the Sheet's edit access is not).
3. Enable Pages: Settings → Pages → Deploy from branch → `main` / root.
4. Contents at launch: `index.html` (map app) · `upload.html` (photo upload page) · `images/` · `CNAME` (when domain exists) · `README.md` pointing to the PRD pack.
## 5. Access Model (who can do what)
 
| Asset | Access | How granted |
|---|---|---|
| Live site content (entries) | Editorial team edit; world reads | Google Sheet sharing, from project Gmail |
| Photos / site code | Team commit; world reads | GitHub collaborators, from project account |
| Photo uploads via `upload.html` | Each editor individually | Personal fine-grained token (Appendix A of Architecture PRD) — per person, revocable per person |
| Submissions queue | Editorial team | Same Sheet sharing as above |
| Domain / DNS | Project account holder(s) only | Registrar login = project email |
| Project account passwords | Whole team (see §6) | Shared credential store |
 
Two deliberate properties: **every individual's access is revocable without touching anyone else's** (personal tokens, personal collaborator status, personal Sheet shares), and **no individual's departure removes the project's own access to anything**.
 
## 6. Credential Custody
 
- A single **"Project Keys" document** (or free shared password manager) holds: project Gmail password, GitHub password, GitHub 2FA recovery codes, registrar login. 
- Stored where every core team member can reach it — e.g. a shared Google Drive folder owned by the project Gmail (which makes the Gmail password the one true key; its recovery options in §2 are the backstop).
- GitHub 2FA sits on one member's authenticator app **plus** the saved recovery codes — the codes, not the phone, are the durable access.
- Personal upload tokens are explicitly **excluded**: they live only in each editor's browser and are never written down anywhere shared (Architecture PRD Appendix A).
## 7. Onboarding & Handover
 
**Onboarding a new team member (~10 min):** share the Sheet with their Google account → add them as a GitHub collaborator → they generate their own upload token (Appendix A) → point them at the PRD pack and the §4 content pipeline in the Architecture PRD.
 
**Offboarding:** remove Sheet share → remove collaborator status → they delete their token (or it's revoked from the project account). Nothing else changes.
 
**Annual handover ritual (start of academic year):** confirm two current members hold the Gmail recovery options; rotate the project account passwords; check 2FA recovery codes are still where the Keys document says; confirm domain auto-renewal payment method is current. Fifteen minutes that prevents the account-loss failure mode entirely.
 
## 8. Setup Checklist (one sitting, ~30–45 min, excluding domain)
 
- [ ] Create project Gmail; set recovery email/phone to two team members
- [ ] Create "Project Keys" doc in a Drive folder owned by the project Gmail
- [ ] Create GitHub project account (Free plan) with the project Gmail
- [ ] Enable 2FA; save recovery codes to the Keys doc
- [ ] Create `<username>.github.io` public repo
- [ ] Upload prototype as `index.html`; enable Pages; confirm the site is live
- [ ] Add all team members as collaborators
- [ ] Create the Google Sheet from the Architecture PRD §5 schema (Live + Queue tabs)
- [ ] Create the Google Form; link responses to the Queue tab
- [ ] Each editor: personal GitHub account (if none) + upload token per Appendix A
- [ ] *(When name locks)* register domain under project email; add CNAME + DNS; enable HTTPS
- [ ] Record everything created in the Keys doc
## 9. Success Criteria
 
- Every critical asset (site, code, content, domain) is owned by the project identity, not a person.
- Any single team member can disappear tomorrow with zero loss of access or content.
- A new member is fully onboarded in under 15 minutes using §7 alone.
- The prototype is publicly reachable at the `github.io` URL before the next meeting.
## 10. Open Questions
 
1. **Which registrar** for the `.org.uk`/`.uk` domain (compare renewal price, not just year-one price).
2. **Password manager vs Keys document** — a free shared vault (e.g. Bitwarden free organisation) is more secure than a doc; is the team willing to adopt one more tool?
3. **Project email naming** — blocked on the project name, same as the domain; a neutral placeholder account is acceptable to start, but migrating Google Sheet ownership later is mildly tedious, so deciding the name first is cheaper.
 