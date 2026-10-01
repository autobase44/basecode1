# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves an HTML page at `/` and JSON at `/health`. No database, no external services, no secrets required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000 with `node --watch` for live reload on file changes.
- Source is bind-mounted at `/app`; edits to `server.js` trigger automatic restart.

## Verification
- `curl http://localhost:3000/` — returns the HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` — returns `{"status":"ok"}`.
- Healthcheck in compose probes `/health` via wget.
