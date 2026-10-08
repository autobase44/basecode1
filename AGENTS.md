# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Source is bind-mounted; there is no live-reload dev server (plain `node server.js`), so call `reload_preview` after edits.
- Health check: `GET /health` → `{"status":"ok"}`

## No secrets required
The app has no environment variables beyond `PORT` and no external credentials.
