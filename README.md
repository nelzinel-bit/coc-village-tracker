# CocBuilderWidgetZi Hybrid Sync

## What this version does
- Keeps imported village JSON data local in the browser.
- Continues countdowns locally from the export timestamp.
- Adds a backend connection field and polls the official player profile every 10 minutes while the PWA is open.
- Displays supported official API profile fields: player name/tag, Town Hall, Builder Hall, trophies, XP, heroes, troops, spells and hero equipment.
- The browser never receives the Supercell API token.

## Important API limitations
The official Clash of Clans API is read-only and exposes public player profile data. It does NOT provide building levels, active builder assignments, builder availability, live upgrade finish times or Builder Potion status. Those continue to come from the exported village JSON snapshot. The API has no push/websocket feed; this app polls every 10 minutes while open.

## Deploy the backend securely
1. Deploy this `server.js`, `package.json`, and `Dockerfile` on a server with a stable public outbound IPv4 address (a small VPS is suitable).
2. Create an API token at https://developer.clashofclans.com/ and whitelist the server's stable outbound IP address in the token settings.
3. Set `COC_API_TOKEN` as a server environment secret. Set `ALLOWED_ORIGIN` to your exact GitHub Pages origin, e.g. `https://nelzinel-bit.github.io`.
4. Start with `npm install && npm start` or build with Docker.
5. Confirm `https://YOUR-BACKEND/health` returns `{ "ok": true }`.
6. In the PWA, expand **Live account sync**, enter the backend base URL, then tap **Connect / sync now**.

Do not deploy the token in GitHub, frontend JavaScript, a public `.env` file, or the browser. Do not use a host with changing outbound IP unless you can whitelist its egress range. Supercell tokens are IP-restricted.

## Frontend deployment
Upload the updated `index.html` plus the existing manifest, service worker and icons to the root of your GitHub Pages repository. If GitHub Pages has already deployed the repo, it will rebuild after commit.

## Files
- `index.html`: PWA UI and polling client
- `server.js`: private API proxy
- `package.json`, `Dockerfile`: backend runtime
- `.env.example`: variable names only; no secrets
