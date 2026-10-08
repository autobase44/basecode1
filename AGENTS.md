# Base Code E2E — Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host 3000).
- No live-reload dev server; `node server.js` must be restarted after code changes
  (`docker compose -f docker-compose.base44.yml restart web`, then `reload_preview`).

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## No secrets required
The app has no environment variables beyond `PORT` and no external dependencies.
