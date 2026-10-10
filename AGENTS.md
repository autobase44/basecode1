# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file: `server.js` — serves an HTML page at `/` and a JSON health check at `/health`.

## Setup
- Runtime: Node.js >= 20 (via `node:20-alpine` in `docker-compose.base44.yml`)
- No `npm install` needed — uses only `node:http`.
- No environment variables or secrets required.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. Health check: `GET /health` → `{"status":"ok"}`.

## Notes
- The README says not to change the app content — it's an E2E test fixture.
- No live-reload dev server; `node server.js` is a plain process. Call `reload_preview` after edits.
- Source is bind-mounted at `/app` in the container, so edits are picked up on container restart.
