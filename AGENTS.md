# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Source is bind-mounted; there is no live-reload dev server, so edit `server.js` then run `reload_preview` (or restart the container) to see changes.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.
- No secrets or external credentials required.
