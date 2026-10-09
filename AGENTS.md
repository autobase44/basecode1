# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
- `server.js` serves an HTML page at `/` and JSON at `/health`.
- Port 3000. No env vars required (only optional `PORT`, defaulting to 3000).

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with the repo bind-mounted at `/app`.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits.
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- The README says tests depend on exact content — do not change `server.js` or `package.json` unless asked.
