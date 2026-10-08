# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- The compose uses `node:20-alpine` with the source bind-mounted at `/app`; no image rebuild needed for edits.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after code changes.
- Health check: `GET /health` → `{"status":"ok"}`.

## Notes
- `server.js` binds to `::` (IPv4+IPv6), so `localhost` healthchecks work.
- The README says not to change the app content — tests depend on exact output.
