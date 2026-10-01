# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Web entry point: host port 3000
- Health check: `GET /health` → `{"status":"ok"}`
- Source is bind-mounted; no live-reload dev server (plain `node server.js`). After editing `server.js`, restart the service or call `reload_preview`.

## Notes
- This repo is a test fixture — its content is checked by E2E tests. Avoid changing the served HTML or health response unless explicitly asked.
