# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
- Entry point: `server.js` (plain `node:http`, no framework)
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. Healthcheck probes `GET /health`.

## Notes
- No live-reload dev server; `node server.js` must be restarted after edits (use `reload_preview`).
- No environment variables or secrets required.
