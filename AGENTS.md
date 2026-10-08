# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services, and no secrets.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- The compose file uses `node:20-alpine`, bind-mounts the source, and runs `node server.js`.
- No live-reload dev server: this is a plain `http.createServer`. Call `reload_preview` after edits so the user sees changes (or `docker compose restart web`).

## Verification
- `GET /` — HTML page with heading "Base Code E2E".
- `GET /health` — returns `{"status":"ok"}`.
