# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- The compose file bind-mounts the source and runs `node server.js` directly from a `node:20-alpine` image (no build step needed).
- No live-reload dev server; call `reload_preview` after edits to `server.js`.

## Notes
- The README says tests depend on exact content — avoid changing `server.js` or `package.json` unless explicitly asked.
- Health check: `GET /health` returns `{"status":"ok"}`.
