# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no env vars). Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Source is bind-mounted; `server.js` is run with plain `node` (no live-reload). After editing `server.js`, call `reload_preview` or `docker compose -f docker-compose.base44.yml restart web`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
