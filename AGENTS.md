# Base44 Dev Environment

## Overview
Minimal Node.js app (no dependencies, no database, no external services). A single `server.js` uses Node's built-in `http` module to serve a static page on port 3000 with a `/health` endpoint.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app.
- Runs from bind-mounted source via `node --watch server.js` (live reload on file changes).
- No environment variables or secrets required.
- Health check: `GET /health` → `{"status":"ok"}`.
- Web entry: `GET /` → page with heading "Base Code E2E".

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` (production build); the Base44 compose uses a plain `node:20-alpine` image with the source bind-mounted instead, so edits are reflected live.
- The README says tests depend on exact file content — avoid modifying `server.js`, `package.json`, or `Dockerfile` unless explicitly asked.
