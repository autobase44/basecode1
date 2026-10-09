# AGENTS.md

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file: `server.js` — a plain `http.createServer` serving HTML at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Notes
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits to `server.js`.
- Source is bind-mounted, so changes are visible on container restart without rebuilding.
- No secrets or environment variables required beyond `PORT` (defaults to 3000).
