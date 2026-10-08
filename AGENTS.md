# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file `server.js` serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with source bind-mounted; no build step needed.
- No live-reload dev server — after editing `server.js`, restart with `docker compose -f docker-compose.base44.yml restart web` and call `reload_preview`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## No Secrets Required
This app has no external dependencies and needs no credentials.
