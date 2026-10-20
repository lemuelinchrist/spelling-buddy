# Spelling Buddy

Offline spelling-practice PWA for a P5/P6 pupil preparing for PSLE (Singapore, British spelling).
Hosted on GitHub Pages from `main`, repo root. No build step, no dependencies.

## Files
- `index.html` — the whole app: CSS, markup and JS in one file. Word bank is `RAW_BANK` near the top of the script.
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
