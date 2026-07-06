# Plate Math

A barbell plate loading calculator built as a single-file, offline-first PWA. No build step, no dependencies, no network calls — just static files you can open directly or host on GitHub Pages.

## Files

- `index.html` — the entire app (HTML, CSS, and JS in one file)
- `manifest.json` — PWA install metadata
- `sw.js` — service worker for offline caching
- `icon-192.png`, `icon-512.png` — app icons

All five files need to stay together in the same folder for install/offline mode to work.

## Installing

**Quick local test:** open `index.html` directly in a browser, or serve the folder locally (e.g. `python3 -m http.server` from inside it) and visit `localhost:8000`.

**GitHub Pages:** push this folder to a repo and enable Pages (Settings → Pages → deploy from branch). Once live, open the URL on your phone and use "Add to Home Screen" (iOS Safari) or the install icon in the address bar (Android Chrome) to install it like a native app. After the first load it works fully offline.

## Core screen

Everything lives on one screen — no menus, no tabs.

- **Weight display** — the big number in the middle is your target weight. Tap the **Enter Weight** button to bring up a numpad, or use the small stepper row (±2.5 / 5 / 10 / 45) under the display for quick adjustments.
- **Barbell diagram** — shows exactly which plates go on each side, largest plate inboard (closest to center), smaller plates stacked outward, collar (if enabled) capping the outer end.
- **Breakdown line** — "PER SIDE: 45 + 45 + 10" spells out the diagram in text.
- **Not achievable** — if your target can't be hit exactly with your plate inventory, the breakdown says so and shows the two nearest achievable weights as tappable chips.
- **Recall chips** (top row) — your last 6 computed weights, one tap to reload any of them.

## Warmup ramp

Tap **Warmup Ramp** to turn your current target into a full warmup sequence (empty bar → 40% → 60% → 80% → 90% → work set by default). Swipe the diagram left/right, or use the arrows in the ramp bar, to step through. Each step snaps to the nearest weight your plates can actually build, and your phone gives a short vibration each time you move to a new step — meant to be usable without looking at the screen. Tap **Warmup Ramp** again to exit back to your target weight.

## % of 1RM

Tap **% of 1RM** to open the calculator. Pick a lift (Squat/Bench/Deadlift by default — tap **+ Lift** to add more), enter your 1RM once (it's saved), then tap 70/75/80/85/90% to get an instant plate solution for that percentage. Tap the big result to load it onto the main screen.

## Dumbbell mode

Tap **Dumbbell** to find the nearest dumbbell your gym actually has. Enter a target weight per hand and it matches against your rack's increments (editable at the bottom of that screen — comma-separated list, e.g. `5, 10, 15, 20...`). If there's no exact match, the two nearest weights are shown as tappable alternatives.

## Superset / strip order

Tap **Superset** when you're alternating between two weights on the same bar. Enter Weight A and Weight B and it shows exactly what to strip off and add on per side to go from one to the other — biased to reuse plates already on the bar so you make the fewest possible swaps.

## Settings (gear icon, top right)

- **Units** — lb or kg, with the correct plate set for each.
- **Bar** — Standard (45 lb/20 kg), Lightweight, Women's, EZ Curl, Trap/Hex, or a custom weight.
- **Collars** — toggle on to add competition collar weight (+5 lb / +2.5 kg) into every calculation.
- **Plate inventory** — set how many pairs of each plate you actually own. The calculator will never prescribe more than you have.
- **Warmup ramp %** — edit the percentages and rep counts used to build your ramp.

Everything above persists automatically in the browser's local storage — no account, no sync, no data ever leaves your device.

## Color scheme

Plates are color-coded by weight so you can identify them at a glance without reading labels: currently set to the "Iron Blue" palette (deep blue for 45s, fading through steel tones down to dark grey for the smallest plates), with a blue accent color reserved for the answer and the active ramp step.
