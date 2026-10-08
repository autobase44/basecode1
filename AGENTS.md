# AGENTS.md

## Overview
Minimal Node.js web app (single `server.js`, zero dependencies) used as a Base44 Base Code E2E test fixture. Serves a static HTML page on `/` and JSON on `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts on port 3000.
- Source is bind-mounted into a `node:20-alpine` container; `node server.js` runs directly (no build step, no live-reload needed — restart the container after edits).
- No dependencies, no environment variables, no database, no secrets.

## Verification
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
- Healthcheck in compose uses `wget` against `/health`.
