# Road to May 2

A 26-week marathon training and nutrition plan for two runners.
Race: Sunday 2 May 2027.

Static site — a single `index.html` with no build step and no dependencies.

## Password

The site is gated behind a password. The current one is **`marathon2027`**.

Unlocking is remembered per browser in `localStorage`, so each person types it once.

### Changing it

The page stores a SHA-256 hash, not the password itself. To set a new one, run this
in any browser console:

```js
crypto.subtle.digest('SHA-256', new TextEncoder().encode('yourNewPassword'))
  .then(b => console.log([...new Uint8Array(b)].map(x => x.toString(16).padStart(2, '0')).join('')))
```

Paste the result into `PW_HASH` in `index.html` and push.

### What this gate is and isn't

It keeps casual visitors out of a public URL. It is **not** real security: the whole
page ships to the browser, so anyone who opens devtools can read past it. Don't put
anything here you'd mind a determined person seeing, and don't reuse a password that
protects anything else.

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

| `PW_HASH` | SHA-256 of the site password |

The two athletes are keyed `samar` and `r2` (Manik).
