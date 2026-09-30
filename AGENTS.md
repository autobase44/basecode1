# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no env vars). A single `server.js` file serves an HTML page at `/` and a JSON health check at `/health` on port 3000.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
The compose file bind-mounts the source into a `node:20-alpine` container and runs `node server.js` directly (no build step, no live reload — call `reload_preview` after edits).

## Health Check
`GET /health` returns `{"status":"ok"}`.

## Notes
- The README says not to change the app — it's an E2E test fixture.
- No lockfile exists because there are no npm dependencies.
