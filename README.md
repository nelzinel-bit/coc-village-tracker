# CoC Village Tracker PWA v2

A mobile-first, installable PWA inspired by the supplied village dashboard screenshot.

## Files
- `index.html` — app UI and timer logic
- `manifest.webmanifest` — install metadata
- `sw.js` — offline caching
- `icon-192.png`, `icon-512.png` — app icons

## Install
Host these files on an HTTPS static host (for example GitHub Pages), then open the site in Chrome on Android and choose **Install app** / **Add to Home screen**.

## API token safety
The token field is session-only and is not persisted or sent anywhere. Supercell's public API does not expose live builder timers; API integration requires a secure backend and stable whitelisted IP. Do not put a production API token into a public client-side app.
