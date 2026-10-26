# Sandy Plains Softball Lineup Generator

A web app for Sandy Plains youth softball coaches to instantly generate a batting lineup and fielding rotation for their team. Pick your age group, **8U** or **10U**, on the home page and you'll go straight to the generator built for that division's rules.

## Features

- **One site for every age group** — choose 8U or 10U from the home page, and use the **Age Groups** button in the header to switch at any time
- **Enter players one by one**, each with a name and jersey number (10U also takes optional ranked position preferences)
- **Save/load your roster** to the browser's local storage so you don't have to re-enter it every game; 8U and 10U rosters are saved separately, so one never overwrites the other
- **Auto-generates** a randomized batting order and fielding grid that satisfies all of your age group's rotation rules
- **Persistent Game Info** — date, team names, and field stay visible and editable on both the input and results screens, so a typo doesn't force a regenerate
- **Click-to-swap** any two players in the batting lineup, or any two players in the same inning of the fielding grid
- **Rule validation** with inline error messages — printing is blocked until all violations are resolved
- **PDF export** opens in a new browser tab for printing or saving, with no browser headers or footers
- **Last updated date and What's New** in each generator's footer, showing when it last changed and what's different
- **Responsive design** — works on desktop, tablet, and mobile; on phones, only the fielding grid scrolls sideways, with its Position column pinned and an edge shadow showing when more innings are off-screen
- No installation, no backend, no dependencies to install — just open `index.html`

---

## Age Groups at a Glance

| | 8U | 10U |
|---|---|---|
| Innings generated | 5 | 3 |
| Roster size | 6–12 players | 7–12 players |
| Position preferences | — | Yes, ranked highest first |
| Bench | 1 spot at 12 players | 1 spot at 11 players, 2 at 12 |
| Printout | Batting lineup and fielding grid | Two identical copies on one sheet, each with the batting lineup and fielding grid side by side |

10U generates only the first 3 innings because most games at that level don't reliably go past the 3rd. The coach can adjust fielding by hand for any later innings.

---

## How to Use

### 1. Choose Your Age Group
Open the site and pick **8U** or **10U**. You can come back to the home page at any time with the **Age Groups** button in the top-right corner.

### 2. Enter Game Info
Fill in the game date (it defaults to today), home team name, away team name, and the field. Pick the field from the dropdown (Sandy Plains Fields 1–4, Shaw Park Fields 2–4) or type in any other field name. This card stays visible after you generate a lineup, so you can fix any of these fields at any time without needing to regenerate.

### 3. Add Your Roster
Enter each player's name and jersey number. Use **+ Add Player** to add rows, or the **×** at the end of a row to remove one.

**10U only:** you can also enter each player's ranked position preferences using shorthand, highest preference first (for example `C, 1B, OF`). Tap or hover the **(i)** next to the Position Prefs heading for a reminder:

| Shorthand | Position |
|---|---|
| C | Catcher |
| P | Pitcher |
| 1B | 1st Base |
| 2B | 2nd Base |
| 3B | 3rd Base |
| SS | Short Stop |
| OF | Any outfield spot |

**Save Roster** stores the current roster in the browser's local storage, overwriting anything saved previously for that age group. **Load Saved Roster** appears automatically whenever a saved roster exists and repopulates the rows from it.

### 4. Generate the Lineup
Click **Generate Lineup** to randomly produce:
- A **batting order** (all players, no duplicates)
- A **fielding rotation** that enforces all of your age group's rules below (10U also gives priority to each player's ranked position preferences)

### 5. Adjust if Needed
Click any two rows in the batting lineup to swap them. Click two cells in the same inning of the fielding grid to swap those players (players can't be swapped between innings). Rule violations are flagged in real time.

### 6. Print or Save
Click **Print / Save PDF** to open a clean PDF in a new browser tab. From there, use the browser's built-in PDF viewer to print or download.

---

## Fielding Rules

Each generator enforces its rules automatically. Manual swaps are checked against the same rules in real time.

### 8U

| # | Rule |
|---|------|
| 1 | A player cannot play multiple positions in a single inning |
| 2 | A player cannot play the same position more than once across the 5 innings |
| 3 | Every position must be filled every inning |
| 4 | Every player must play an infield position at least **2 times** per game |

### 10U

| # | Rule |
|---|------|
| 1 | Every position must be filled every inning by a distinct player |
| 2 | Players are placed in their preferred positions where possible, honoring rank order (no player has a bench preference — that's randomized) |
| 3 | A player cannot sit any Bench slot more than once, in aggregate, per game |
| 4 | A player can pitch at most 2 of the 3 innings (not required to be consecutive) |

---

## Fielding Positions by Player Count

### 8U

| Players | Positions |
|---------|-----------|
| 12 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Short Field, Left Field, Left Center Field, Right Center Field, Right Field, Bench |
| 11 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Short Field, Left Field, Left Center Field, Right Center Field, Right Field |
| 10 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Short Field, Left Field, Center Field, Right Field |
| 9 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Short Field, Left Field, Right Field |
| 8 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Short Field, Outfield |
| 7 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Short Field |
| 6 | Pitcher, Catcher, 1st Base, 2nd Base, Short Stop, 3rd Base |

### 10U

| Players | Positions |
|---------|-----------|
| 12 | Catcher, Pitcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Left Field, Left Center Field, Right Center Field, Right Field, Bench 1, Bench 2 |
| 11 | Catcher, Pitcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Left Field, Left Center Field, Right Center Field, Right Field, Bench |
| 10 | Catcher, Pitcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Left Field, Left Center Field, Right Center Field, Right Field |
| 9 | Catcher, Pitcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Left Field, Center Field, Right Field |
| 8 | Catcher, Pitcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Left Field, Right Field |
| 7 | Catcher, Pitcher, 1st Base, 2nd Base, Short Stop, 3rd Base, Outfield |

With 10 or fewer players in 10U, every player fields a position every inning and there is no bench.

---

## What's in This Repository

| Path | What it is |
|---|---|
| `index.html` | Home page where you choose an age group |
| `8u/index.html` | 8U lineup generator |
| `10u/index.html` | 10U lineup generator |
| `8u/CHANGELOG.md`, `10u/CHANGELOG.md` | History of changes to each generator |
| `assets/` | Logo used on the home page |

Each generator is a single self-contained HTML file. All links between pages are relative, so the site works the same whether it's opened from a downloaded folder or hosted (for example on GitHub Pages).
