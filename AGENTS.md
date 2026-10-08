# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Web entry point: port 3000
- Health check: `GET /health` → `{"status":"ok"}`
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits.

## Notes
- Source is bind-mounted; changes to `server.js` require a container restart or preview reload.
- No secrets or environment variables needed.
