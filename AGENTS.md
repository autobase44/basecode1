# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 inside the container.
- No dependencies to install — `node server.js` runs directly from the bind-mounted source.
- No live-reload dev server; after editing `server.js`, restart the service or call `reload_preview`.

## Health Check
- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the HTML page with heading "Base Code E2E".

## Notes
- No environment variables or secrets required.
- The repo's own `Dockerfile` bakes source via `COPY` (production-style); the Base44 compose bind-mounts source instead so edits are reflected.
