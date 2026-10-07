# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`. No database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped from container).
- No live-reload dev server; this is a plain `node server.js` process. Use `reload_preview` after code changes.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Constraints
- The README asks not to change `server.js` or `package.json` — tests depend on exact content.
