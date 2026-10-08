# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no env vars). Single `server.js` using `node:http`.

## Setup
- Runs via `docker-compose.base44.yml` using `node:20-alpine` with source bind-mounted at `/app`.
- Uses `nodemon` (installed globally at container startup) for live reload on `server.js` changes.
- Port 3000 serves the app; `/health` returns `{"status":"ok"}`.
- No secrets or external services required.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `docker compose -f docker-compose.base44.yml ps` → container status `healthy`
