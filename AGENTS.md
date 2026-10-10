# AGENTS.md

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single `server.js` using only `node:http`.

## Running in Base44
- `docker compose -f docker-compose.base44.yml up -d` — uses `node:20-alpine` with source bind-mounted at `/app`.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits.
- Web entry point on host port 3000; `/health` returns `{"status":"ok"}`.
- No secrets or environment variables required.
