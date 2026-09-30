# AGENTS.md

## Overview
Minimal Node.js web app (`server.js`) — no dependencies, no database, no environment variables.
Serves a static HTML page at `/` and `{"status":"ok"}` at `/health` on port 3000.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the repo bind-mounted at `/app`; runs `node server.js` directly from source.
- No `npm install` needed — `package.json` has zero dependencies.

## Notes
- No live-reload dev server; `server.js` is run directly. After editing source, call `reload_preview` (or restart the container) to reflect changes.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.
