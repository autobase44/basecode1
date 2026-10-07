# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external credentials. Serves a static HTML page at `/` and `{"status":"ok"}` at `/health`. Listens on port 3000.

## Running
```sh
docker compose -f docker-compose.base44.yml up -d
```
The compose file bind-mounts the repo source into a `node:20-alpine` container and runs `node server.js` directly (no build step, no live-reload framework). After editing `server.js`, call `reload_preview` to refresh.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- The README warns not to change the app content — E2E tests depend on it.
