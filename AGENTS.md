# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no env vars, no secrets).
Serves a static HTML page at `/` and `{"status":"ok"}` at `/health` on port 3000.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with source bind-mounted at `/app`.
- Runs `node --watch server.js` for live reload on edits.
- Healthcheck: `GET /health`.

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` (production build) — do not use it for dev.
- No `npm install` needed; the app uses only Node built-in modules.
