# CoC Village Tracker PWA v3

Mobile-first installable PWA inspired by the supplied dashboard screenshot.

## Importing your village
Open the app, expand **Import village JSON**, choose the JSON export file or paste the exported JSON, then tap **Import village data**. The app reads the player tag and currently exported timer/cooldown fields. Imported timers are calculated from the export timestamp and count down locally.

## Important limitations
- The export may contain upgrade timers for heroes, buildings, pets, spells, troops and helper cooldowns; not every item is necessarily a builder upgrade.
- Timer names are identified only where IDs are confidently mapped. Unrecognized IDs are shown as numeric IDs rather than guessed.
- This is an export snapshot, not a live sync. Re-export/import to refresh it.
- The API token is not sent or persisted. Never expose a Supercell API token in public client-side code.
- PWA countdowns update while the app is open; browser background execution and notifications are not guaranteed.

## Install
Host all files on HTTPS (e.g. GitHub Pages), then open in Android Chrome and choose Install app / Add to Home screen.
