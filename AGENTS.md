# Base44 Dev Environment

## Project
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services. Serves a single HTML page at `/` and a JSON health check at `/health`.

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the repo bind-mounted at `/app`; runs `node server.js` directly (no dev framework, so no live reload — call `reload_preview` after edits).
- No secrets required.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- Healthcheck in compose probes `/health` via `wget`.
