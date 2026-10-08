# Base44 Dev Environment

## Overview
Minimal Node.js web app (test fixture). No dependencies, no database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The container uses `node:20-alpine` with the repo bind-mounted at `/app`; `node server.js` runs directly from source.
- No live-reload dev server exists (raw `http.createServer`). After editing `server.js`, call `reload_preview` or restart the container: `docker compose -f docker-compose.base44.yml restart web`.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
