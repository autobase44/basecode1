# AGENTS.md

## Project Overview
Minimal Node.js HTTP server (no dependencies, no framework, no database). Serves a static HTML page at `/` and a JSON health check at `/health`.

## Setup
- Runs via `docker compose -f docker-compose.base44.yml up -d` using the `node:20-alpine` image with the source bind-mounted at `/app`.
- No environment variables or secrets required. `PORT` defaults to 3000.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after source edits.

## Verification
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
