# Base44 Dev Environment

## Project
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a page at `/` and a health check at `/health` on port 3000.

## Setup
- `docker compose -f docker-compose.base44.yml up -d --build` brings up the app.
- No database, no external services, no secrets required.
- The app runs from bind-mounted source at `/app` inside the container.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
