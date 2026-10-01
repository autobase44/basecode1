# Base44 Dev Environment

## Overview
Minimal zero-dependency Node.js HTTP server (`server.js`) used as a Base44 E2E test fixture.
- No npm dependencies, no database, no external services, no secrets required.
- `GET /` serves an HTML page; `GET /health` returns `{"status":"ok"}`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher, no extra dependencies).
- Source is bind-mounted at `/app`, so edits are reflected without rebuilding.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
