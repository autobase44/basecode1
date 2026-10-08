# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- The app runs from bind-mounted source via `node server.js` (no build step, no live-reload framework — call `reload_preview` after edits).
- Web entry point: port 3000.
- Health check: `GET /health` returns `{"status":"ok"}`.

## Secrets
None required.
