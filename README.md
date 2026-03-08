# 2026mabil Scouting Dashboard

A lightweight, self-contained HTML scouting analysis tool for the 2026 Abilene district event. No server required — just open the file in any browser.

🔗 **Live site:** https://davepowers.github.io/2026MABIL/

---

## Files

| File | Description |
|------|-------------|
| `index.html` | Main dashboard — team browser + compare tool (GitHub Pages entry point) |

---

## index.html — Main Dashboard

The main dashboard has two tabs.

### Tab 1 — Team Browser

Browse all 29 scouted teams from the event. Teams are listed on the left panel, sorted by average points contribution, with tier badges:

- 🟡 **Elite** — 70+ avg pts
- 🟢 **Strong** — 40–69 avg pts
- 🔵 **Mid** — 20–39 avg pts
- 🟣 **Low** — 5–19 avg pts
- 🔴 **Struggling** — under 5 avg pts

Use the search box to jump straight to a team number. Clicking a team shows:

- **Summary stats** — avg total, auto, and tele pts, hub accuracy, reliability %, std deviation, min/max range, and driver rating
- **Points per match chart** — line chart across all scouted matches; malfunction matches are highlighted in red, comms issues in yellow
- **Auto vs Tele breakdown chart** — stacked bar per match so you can see how each period contributes
- **Match-by-match table** — every scouted match with total/auto/tele pts, hub accuracy, bot status, and full scout notes

### Tab 2 — Compare Teams

Pick any 3 teams from the dropdowns and hit **Update Charts** to generate:

- **Points per match** — overlaid line chart showing trajectories across the event
- **Avg auto vs tele** — grouped bar comparing where each team scores
- **Hub fuel accuracy** — horizontal bar
- **Ratings radar** — spider chart across driver rating, fuel intake rating, accuracy, reliability, and consistency
- **Score range** — shows min/max spread with average marked per team

---

## Data Source

Data was exported from the 6328 scouting app and covers qualifying matches 1–41 at the 2026 Abilene district event (`2026mabil`). Each team has between 8–9 scouted matches. Metrics include:

- Points contribution (alliance-relative)
- Hub fuel success/fail counts and accuracy
- Auto and teleop breakdowns
- Climb points
- Bot state (No Issue / Comms Issue / Brownout / Major Malfunction)
- Driver, fuel intake, and defense ratings (scout-assigned, 0–4 scale)
- Scout notes and start positions

---

## Notes

- All data is embedded directly in the HTML — no internet connection or external files needed
- Charts are powered by [Chart.js](https://www.chartjs.org/)
- Points contribution is expressed as a percentile of the alliance total, not raw points
