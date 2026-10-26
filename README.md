# Sandy Plains Softball Lineup Generator

One website for youth softball coaches that holds the lineup generators for each age group. The home page asks the coach to choose **8U** or **10U**, then opens that age group's generator. Each generator works exactly like its standalone version.

## Project Structure

```
SPSA-lineup-generator/
├── index.html          Home page: choose 8U or 10U
├── assets/
│   └── softball.png    Logo used on the home page
├── 8u/
│   ├── index.html      8U generator (5 innings)
│   ├── SKILL.md        8U spec and rules
│   └── CHANGELOG.md    8U change history
└── 10u/
    ├── index.html      10U generator (3 innings)
    ├── SKILL.md        10U spec and rules
    └── CHANGELOG.md    10U change history
```

Each age group's `index.html` is still a single self-contained file. The only change from the standalone versions is an **Age Groups** button in the header that links back to the home page.

## Age Groups

| | 8U | 10U |
|---|---|---|
| Innings generated | 5 | 3 |
| Roster size | 6–12 players | 7–12 players |
| Position preferences | No | Yes, ranked |
| Key rules | No repeat positions; every player plays infield at least twice | Pitch at most 2 innings; bench at most once |

See `8u/SKILL.md` and `10u/SKILL.md` for the full rules and fielding positions by player count.

## Saved Rosters

Each age group saves its roster under its own browser storage key, so an 8U roster and a 10U roster never overwrite each other, even though both sites share one domain.

## Running It

No build step and no dependencies. Open `index.html` in a browser, or host the folder as-is (for example on GitHub Pages). All links are relative, so the site works from a local folder or any web address.
