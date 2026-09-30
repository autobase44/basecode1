# AGENTS.md

## Project overview
Minimal single-file Node.js app (`server.js`) — no dependencies, no database, no environment variables required. Serves a static HTML page at `/` and a JSON health check at `/health`. Used as a Base44 E2E test fixture; do not change the page content (tests depend on the heading "Base Code E2E").

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload — edits to `server.js` are picked up automatically.
- Healthcheck probes `GET /health` (returns `{"status":"ok"}`).

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with `<h1>Base Code E2E</h1>`
