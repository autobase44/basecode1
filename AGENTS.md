# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables required. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The compose uses `node:20-alpine` with the source bind-mounted at `/app` and runs `node server.js` directly (no build step, no live-reload dev server — use `reload_preview` after edits).
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Notes
- The README says the app content is a test fixture — avoid changing `server.js`, `package.json`, or `README.md` unless explicitly asked.
- No secrets or external credentials are needed.
