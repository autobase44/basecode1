# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and JSON at `/health`. No database, no external services, no secrets required.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
The app listens on port 3000. Health check: `GET /health` → `{"status":"ok"}`.

## Notes
- No live-reload dev server (plain `node server.js`). After editing `server.js`, call `reload_preview` to reflect changes.
- The Dockerfile bakes source via `COPY`; the Base44 compose instead bind-mounts the repo so edits are visible without rebuilding.
