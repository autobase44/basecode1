# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services, no environment variables. Serves a single HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build` starts the app on port 3000.
- The source is bind-mounted; there is no live-reload dev server, so call `reload_preview` after editing `server.js`.
- Health check: `GET /health` returns `{"status":"ok"}`.

## Notes
- The app has zero npm dependencies — no install step is needed.
- No secrets or external credentials are required.
