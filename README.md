# Road to May 2

A 26-week marathon training and nutrition plan for two runners.
Race: Sunday 2 May 2027.

Static site — a single `index.html` with no build step and no dependencies.

## Deploying to Vercel

Import the repo in Vercel and accept the defaults:

- Framework preset: **Other**
- Build command: *(leave empty)*
- Output directory: *(leave empty — it serves the repo root)*

If the site lives in a subdirectory of the repo, set **Root Directory** to that folder.

## Editing

Everything lives in `index.html`. The plan data is in the `<script>` block near
the bottom:

| Constant | What it holds |
|---|---|
| `WEEKS` | All 26 weeks — `[week, km, longRun, phaseIndex, isDownWeek]` |
| `CAL` | Phase 1 day-by-day — `[tue, thu, satLong, sun, noteKey]` |
| `ATH` | Both athletes: weights, calorie phases, food amounts |
| `FOOD` | The shared food list; `rice`/`alm`/`ban`/`kri` scale per athlete |
| `PHASES` | Phase names and date ranges |

Change `ATH.r2.label` to the second runner's name.
