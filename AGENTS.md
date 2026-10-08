# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Serves an HTML page at `/` and JSON `{"status":"ok"}` at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The container uses `node --watch server.js` for live reload on file changes.
- Source is bind-mounted from the repo root into `/app`.
- Healthcheck probes `http://localhost:3000/health`.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Secrets
None required. No external services, no database.
