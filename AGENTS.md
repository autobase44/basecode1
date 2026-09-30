# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no env vars). Single `server.js`
serves an HTML page at `/` and JSON at `/health` using only `node:http`.

## Running
`docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
The compose service uses `node --watch server.js` for live reload on file changes.

## Verification
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` — do not use it for dev; the
  Base44 compose bind-mounts source and runs `node --watch` instead.
- No external credentials or secrets are required.
