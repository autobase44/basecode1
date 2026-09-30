# AGENTS.md

## Overview
Minimal single-file Node.js web app (no dependencies, no database, no external services).
- `server.js` — plain `http.createServer` serving `/` (HTML page) and `/health` (JSON).
- No build step, no package manager dependencies.

## Running
- `docker compose -f docker-compose.base44.yml up -d` (bind-mounts source into `node:20-alpine`, runs `node server.js`).
- Web entry point on port 3000; healthcheck at `GET /health` → `{"status":"ok"}`.

## Editing
- No live-reload dev server. After editing `server.js`, restart the container:
  `docker compose -f docker-compose.base44.yml restart web`, then `reload_preview`.
- Source is bind-mounted, so changes appear after a restart without rebuilding the image.

## No secrets required
No environment variables beyond `PORT` (defaulted to 3000) are needed.
