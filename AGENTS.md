# Base44 Dev Environment

## App overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Base image: `node:20-alpine`; source is bind-mounted at `/app`, so edits to `server.js` require a container restart (no live-reload framework).
- After editing `server.js`, run `docker compose -f docker-compose.base44.yml restart web` then `reload_preview`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- This repo is an E2E test fixture; its content is intentionally minimal and should not be changed beyond what's asked.
