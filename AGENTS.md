# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). A single `server.js` serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The container uses `node:20-alpine` with the repo bind-mounted at `/app`; edits to `server.js` require a container restart (no live-reload dev server — plain `node server.js`).
- After a code change, call `reload_preview` so the user sees the update.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}`.

## Notes
- No environment variables or secrets are required.
- No package dependencies (`npm install` is unnecessary).
