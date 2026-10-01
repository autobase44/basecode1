# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- The source is bind-mounted into the container, so edits to `server.js` are picked up on container restart (there is no file watcher / hot reload).
- After editing `server.js`, restart the `web` service or call `reload_preview` to see changes.

## Verification
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.

## Notes
- No external credentials, no database, no environment variables required beyond `PORT`.
- The repo's `Dockerfile` bakes source via `COPY` (production build) — do not use it for dev; the compose file uses a plain `node:20-alpine` image with a bind mount instead.
