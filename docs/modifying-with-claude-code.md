# Modifying AdvantageData with Claude Code

A guide for non-programmers who want to customize or add features to the scouting dashboard.

---

## What you're working with

The entire app is a single file: **`index.html`**. There is no separate server, no database, no build process. To make changes, you edit that one file. To see your changes, you refresh a browser tab.

That's it.

---

## Step 1 — Open the project in Claude Code

1. Open your terminal (on Mac: press `Cmd + Space`, type "Terminal", press Enter)
2. Navigate to the project folder:
   ```
   cd ~/Projects/FRC/advatalytics
   ```
3. Launch Claude Code:
   ```
   claude
   ```

You are now in Claude Code with the project loaded. Claude can read, understand, and edit `index.html` on your behalf.

---

## Step 2 — Preview the app in your browser

Before making any changes, open the app so you can see what your changes look like:

1. In Finder, navigate to the project folder
2. Double-click `index.html`
3. It will open in your default browser

After Claude makes a change, press **Cmd + R** (Mac) or **F5** (Windows) in the browser to refresh and see the update.

> **Note:** The Match Analysis tab requires an internet connection (it loads live data from Statbotics). The rest of the app works fully offline.

---

## Step 3 — Ask Claude to make changes

Just describe what you want in plain English. You do not need to know how to code. Claude will find the right place in `index.html` and make the edit.

### Example requests

**Adding or changing displayed information:**
> "Add a column to the match table that shows the scout's name"

> "Show the team's best single-match score next to their average in the team list"

> "Add a 'defense rating' bar to the team detail page"

**Changing how things look:**
> "Make the tier badges larger and easier to read"

> "Change the color of the Elite tier badge from yellow to gold"

> "Add a dividing line between the auto and tele sections of the match table"

**Adding new features:**
> "Add a notes section where I can type and save a comment about a team that persists when I reload the page"

> "Add a button that exports the pick list to a text file"

> "Add a toggle that hides teams with fewer than 5 scouted matches"

**Changing data or configuration:**
> "Add team 9999 to the team list"

> "Change the event code from 2026mabil to 2026txhou"

---

## Step 4 — Review and test the change

After Claude makes an edit:

1. Refresh your browser (`Cmd + R`)
2. Click around the part of the app that was changed
3. If something looks wrong, describe the problem to Claude: *"The new column is showing 'undefined' instead of the scout name"*

Claude can fix mistakes when you describe what you see.

---

## How `index.html` is organized (useful context to give Claude)

When asking for changes, it helps to know the basic layout of the file. You do not need to understand the code — just knowing the section names lets you give Claude more precise instructions.

| Section | What it does |
|---------|-------------|
| `<style>` block (top of file) | All the visual styling — colors, fonts, spacing, layout |
| `ALL_TEAMS` | The hardcoded list of team numbers for this event |
| `SCOUTING_DATA` | All scouted match data, embedded directly in the file |
| `TEAM_PHOTOS` | Paths to robot photos for each team |
| `buildTeamList()` | Renders the team list on the left/drawer |
| `renderTeamDetail()` | Renders everything on the right when you click a team |
| `renderCompare()` | Builds all the charts on the Compare tab |
| `loadMatchAnalysis()` | Fetches live match data from Statbotics |
| `processCSVRows()` | Parses an uploaded CSV file into scouting data |
| `localStorage` references | Where pick list, DNP list, and hidden teams are saved between sessions |

Example of using this context in a prompt:
> "In the `renderTeamDetail` section, add a line that shows the team's average defense rating if it's greater than 0"

---

## Giving Claude useful context

The more specific you are, the better the result. Compare:

| Vague | Specific |
|-------|----------|
| "Fix the charts" | "The line chart on the Compare tab cuts off the last match — make it show all matches" |
| "Make it look better" | "Make the stat cards on the team detail page slightly larger with more padding" |
| "Add a feature" | "Add a star button next to each team in the list that I can toggle to mark favorites, saved to localStorage" |

If you're unsure how to describe something, take a screenshot and paste it into Claude with a description of what's wrong or what you want.

---

## Saving your changes

Claude edits the file directly on disk. Your changes are saved automatically every time Claude makes an edit. You do not need to press save.

If you want to undo a change, you can ask Claude: *"Undo the last change"* — or, if you use git, run `git diff` to see what changed and `git checkout index.html` to revert to the last committed version.

---

## Deploying changes to the live site

The live dashboard is hosted on GitHub Pages at `https://davepowers.github.io/2026MABIL/`. To push your changes there:

1. Ask Claude: *"Commit my changes and push to main"*
2. Claude will create a git commit and push — the site updates automatically within a minute or two

> Claude will describe what it's about to commit and ask for confirmation before pushing.

---

## Quick reference: things Claude can help with

- **Add a new stat** to the team detail view or match table
- **Change a color or font** anywhere in the app
- **Add a new tab** with custom content
- **Modify the tier thresholds** (e.g. change Elite from 70+ to 80+)
- **Add new CSV fields** from an updated scouting app export
- **Change which teams are listed** for a new event
- **Add keyboard shortcuts** for power users
- **Export data** to CSV, clipboard, or a shareable format
- **Add a notes/annotation system** saved to localStorage
