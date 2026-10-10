# Base44 Dev Environment

## Setup
- Single Node.js service (`server.js`), no dependencies, no database, no external credentials.
- Runs via `docker-compose.base44.yml` using `node:20-alpine` with source bind-mounted at `/app`.
- Dev command: `node --watch server.js` (Node built-in file watcher for live reload).
- Port 3000 is the web entry point; `/health` returns `{"status":"ok"}`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
