# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no external services. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
The app listens on port 3000. The compose file bind-mounts the repo into a `node:20-alpine` container and runs `node server.js` directly (no live-reload dev server exists in this project).

## Notes
- No `.env`, no secrets, no migrations or seeds needed.
- After editing `server.js`, call `reload_preview` — there is no file watcher.
- Health check: `GET /health` returns `{"status":"ok"}`.
