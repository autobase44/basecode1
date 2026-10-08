# Base44 Setup Notes

## Overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no env vars).
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (binds all interfaces).
- No live-reload dev server; restart the `web` service after code changes (`docker compose -f docker-compose.base44.yml restart web`), then call `reload_preview`.

## Constraints
- The README says **do not change** `server.js` or `package.json` — E2E tests depend on their exact content.
