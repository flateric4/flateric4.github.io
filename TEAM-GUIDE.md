# This Place Counts — Team Guide

Hey team! Here's everything you need to know about how the site works.

## The short version

The website is a map that reads from a Google Sheet. You edit the Sheet, the website updates itself. That's it — no code, no developer needed.

**Live website:** https://flateric4.github.io
**Google Sheet:** https://docs.google.com/spreadsheets/d/1c_jzcPq_0m9RcF7LhUlhn_4vlVfh62h4wQMi6mz3aoQ/edit
**GitHub repo (you probably won't need this):** https://github.com/flateric4/flateric4.github.io


## Adding a new entry to the map

1. Open the [Google Sheet](https://docs.google.com/spreadsheets/d/1c_jzcPq_0m9RcF7LhUlhn_4vlVfh62h4wQMi6mz3aoQ/edit)
2. Make sure you're on the **Live** tab (bottom of the screen)
3. Fill in a new row at the bottom — here's what goes in each column:

| Column | What to write | Example |
|---|---|---|
| **name** | What's the place called? | Bridge Park Complex |
| **lat** | Latitude (see below for how to find this) | 51.548 |
| **lng** | Longitude | -0.265 |
| **location** | Where is it, in plain English? | Stonebridge, Brent, London |
| **tags** | Which heritage type? Use the codes below | dia,wc |
| **description** | Tell the story of this place | A pioneering Black-led community centre... |
| **references** | Your sources, separated by semicolons | Historic England report; GLA survey 2019 |
| **status** | Is it still there? Use: extant, at risk, or demolished | at risk |
| **photo** | Photo filename (if we have one — fine to leave blank) | bridge-park.jpg |
| **published** | Ready to go live? Put yes (or leave blank — it'll show either way) | yes |

4. The Sheet saves automatically — just refresh the website and your new dot should be on the map!

### Tag codes

These go in the **tags** column. You can use more than one, separated by commas (e.g. `ind,wc`). The first one sets the dot colour.

| Type this | What it means | Dot colour on the map |
|---|---|---|
| `wc` | Working-class heritage | Orange |
| `ind` | Industrial heritage | Blue |
| `dia` | Diaspora heritage | Pink |
| `tra` | Traveller heritage | Green |

### How to find the latitude and longitude

Don't worry, this is easy:

1. Open [Google Maps](https://maps.google.com)
2. Find the location and **right-click** on it (or long-press on your phone)
3. You'll see two numbers at the top of the menu (something like `51.548, -0.265`) — click them to copy
4. The first number goes in the **lat** column, the second in **lng**


## Editing an existing entry

Just open the Sheet and change whatever you need. Next time someone loads the website, they'll see the update.


## Want to hide an entry without losing it?

Put `no` in the **published** column. It stays in the Sheet for the record but disappears from the map. Change it back to `yes` whenever you're ready to show it again.


## Adding photos

This part uses GitHub, but it's just drag and drop:

1. Go to the [images folder on GitHub](https://github.com/flateric4/flateric4.github.io/tree/main/images)
2. Click **Add file** then **Upload files**
3. Drag your photo in and click the green **Commit changes** button
4. Back in the Sheet, type the filename (e.g. `bridge-park.jpg`) in the **photo** column

(Photos aren't wired up on the site just yet — coming soon!)


## A few things to keep in mind

- **The Sheet is everything.** If something looks wrong on the website, the fix is almost certainly in the Sheet.
- **Rebecca has final say** on all wording, narrative, and what gets published.
- **Fact-check and reference every entry** before publishing — the project's credibility depends on it.
- **Prefer hiding over deleting.** If you're unsure about an entry, set published to `no` rather than deleting the row. If something does go wrong, the Sheet keeps version history — go to File, then Version history to roll back.
