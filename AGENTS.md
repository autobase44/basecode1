# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.
Serves an HTML page at `/` and a health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs from the cloned source (bind-mounted), on a plain `node:20-alpine` image.
- No live-reload dev server (the project has none); run `reload_preview` after edits to `server.js`.
- No environment variables or secrets required.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- Healthcheck in compose probes `/health` via wget.

## Notes
- The README asks not to change the app content (it is an E2E test fixture).
