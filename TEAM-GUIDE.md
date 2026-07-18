# This Place Counts — Team Guide

## What is this?

An interactive map of the UK's overlooked heritage, live at:

**https://flateric4.github.io**

The map pulls its data from a shared Google Sheet. When you edit the Sheet, the changes appear on the website the next time someone loads the page. No code, no uploading, no waiting for a developer.


## Key links

| What | Link |
|---|---|
| Live website | https://flateric4.github.io |
| Google Sheet (edit entries) | https://docs.google.com/spreadsheets/d/1c_jzcPq_0m9RcF7LhUlhn_4vlVfh62h4wQMi6mz3aoQ/edit |
| GitHub repo (site code) | https://github.com/flateric4/flateric4.github.io |


## How to add a new entry

1. Open the Google Sheet (link above)
2. Go to the **Live** tab at the bottom
3. Add a new row at the bottom with these columns:

| Column | What to put | Example |
|---|---|---|
| **name** | Name of the site or project | Bridge Park Complex |
| **lat** | Latitude (decimal) | 51.548 |
| **lng** | Longitude (decimal) | -0.265 |
| **location** | Human-readable place name | Stonebridge, Brent, London |
| **tags** | One or more tag codes, comma-separated | dia,wc |
| **description** | The entry text | A pioneering Black-led community centre... |
| **references** | Sources, separated by semicolons | Historic England report; GLA survey 2019 |
| **status** | One of: extant / at risk / demolished | at risk |
| **photo** | Filename if a photo has been uploaded | bridge-park.jpg |
| **published** | yes or no (leave blank to show by default) | yes |

4. Save the Sheet (it saves automatically)
5. Refresh the website — your new entry should appear on the map

### Tag codes

Use these short codes in the **tags** column:

| Code | Meaning | Dot colour |
|---|---|---|
| wc | Working-class heritage | Orange |
| ind | Industrial heritage | Blue |
| dia | Diaspora heritage | Pink |
| tra | Traveller heritage | Green |

An entry can have multiple tags, separated by commas (e.g. `ind,wc`). The first tag determines the dot colour on the map.

### Finding latitude and longitude

1. Go to Google Maps
2. Right-click (or long-press on mobile) on the location
3. The lat/lng numbers appear at the top of the menu — click to copy
4. Paste into the **lat** and **lng** columns (they'll be two numbers separated by a comma — put the first in lat, the second in lng)


## How to edit an existing entry

Just change the text in the Sheet. The website will pick up the change on the next page load.


## How to hide an entry without deleting it

Set the **published** column to `no`. The entry stays in the Sheet but won't appear on the map.


## How to add a photo

1. Go to the GitHub repo: https://github.com/flateric4/flateric4.github.io
2. Click the **images** folder
3. Click **Add file → Upload files**
4. Drag in your photo and click **Commit changes**
5. In the Sheet, put the filename (e.g. `bridge-park.jpg`) in the **photo** column for that entry

Photos are not yet wired up in the current version — this will be connected soon.


## Important notes

- **The Sheet is the single source of truth.** Everything on the map comes from the Sheet. If something looks wrong on the site, check the Sheet first.
- **All content is Rebecca's domain.** Final wording, narrative, and what gets published is her call.
- **Every entry must be fact-checked and referenced** before it goes live. The project's credibility depends on this.
- **Don't delete rows** unless you're sure — use the published column to hide entries instead. The Sheet has version history (File → Version history) if anything goes wrong.
