# AGENTS.md

## Project Overview
Minimal Node.js web app (single file `server.js`, zero npm dependencies) used as a Base44 E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the repo bind-mounted at `/app`; no build step needed.
- No live-reload dev server — `node server.js` is a plain process. Call `reload_preview` after edits.
- No database, no external services, no secrets required.

## Health Check
- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the HTML page with heading "Base Code E2E".

## Notes
- The server binds to `::` (IPv4+IPv6), so `localhost` healthchecks work.
- Do not change the app's content — E2E tests depend on the exact heading and structure.
