# Base44 Setup Notes

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page on port 3000 and `GET /health` returns `{"status":"ok"}`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App is served on host port 3000.
- No live-reload dev server — `server.js` is a raw `http.createServer`. After editing source, call `reload_preview` so the user sees the change (restart the `web` service first).
- No secrets or environment variables required.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
