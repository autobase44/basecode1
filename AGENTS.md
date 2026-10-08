# Base44 Setup Notes

## Overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no environment variables).

- `npm start` runs `node server.js`, serving HTML on port 3000.
- `GET /` → page with heading "Base Code E2E".
- `GET /health` → `{"status":"ok"}`.

## Running in the sandbox
`docker compose -f docker-compose.base44.yml up -d` starts the app via `docker-compose.base44.yml`.
The source is bind-mounted into a `node:20-alpine` container; no image rebuild is needed for edits.
There is no live-reload dev server — after editing `server.js`, restart the service or call `reload_preview`.

## Verification
- `curl http://localhost:3000/` should return HTML containing "Base Code E2E".
- `curl http://localhost:3000/health` should return `{"status":"ok"}`.
