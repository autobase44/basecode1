# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. Health check at `GET /health` → `{"status":"ok"}`.

## Notes
- No `node_modules` — uses only Node built-ins (`node:http`).
- No live-reload: `server.js` runs directly with `node`. Restart the container after edits: `docker compose -f docker-compose.base44.yml restart app`.
- No secrets or environment variables required.
