# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file `server.js` serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- Source is bind-mounted from the repo root into the container at `/app`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Secrets
None required.
