# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no env vars). Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted; there is no live-reload dev server (plain `node server.js`), so call `reload_preview` after code changes.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Constraints
- The README says tests depend on exact file content — do not change `server.js` or `package.json` unless explicitly asked.
