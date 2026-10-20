# Spelling Buddy

Offline spelling-practice PWA for two children in Singapore (British spelling): a P5/P6 pupil preparing
for PSLE on a phone, and a P3 pupil on a tablet. Hosted on GitHub Pages from `main`, repo root.
No build step, no dependencies.

## Levels
- Each device picks a level on first run (`S.level`: `p3` or `p56`), changeable in Words → Settings.
  There are no profiles: one child per device.
- `LEVELS` holds each level's word bank, default daily goal and wording. Banks are `RAW_BANK_P3` and `RAW_BANK_P56`.
- Saved data from before levels existed is treated as `p56`.
- Copy is child-neutral (no "her"/"his"); child-facing screens address the child as "you".
- Must work at phone width (~390px) and on tablets in portrait and landscape (layout widens at 700px).

## Files
- `index.html` — the whole app: CSS, markup and JS in one file. Word banks are near the top of the script.
- `sw.js` — service worker. Cache-first, so the app opens with no connection.
- `manifest.webmanifest`, `icons/` — install metadata and icons.
- `fonts/` — Fredoka and Nunito (latin subset), bundled so nothing is fetched from the internet.

## Rules for every change
- **Bump `VERSION` in `sw.js` on every commit that changes any shipped file.** Phones only pick up a new version when sw.js changes.
- If you add or rename a shipped file, add it to `ASSETS` in `sw.js`.
- Everything must work offline: no CDN scripts, web fonts or remote images.
- Progress lives in `localStorage` under `spellbuddy.v1`. Never change its shape in a way that loses existing data; migrate it instead.
- The app updates itself at a calm moment (not mid-practice); keep that behaviour.

## History
Started as a Claude artifact. That copy has a "Move progress to another device" backup code used to migrate to this site.
