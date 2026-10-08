# Base44 Setup Notes

## Overview
Minimal Node.js web app (single `server.js` file, no dependencies, no database, no env vars).

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, binds all interfaces (`::`).
- Live reload via Node 20 built-in `--watch` mode — edits to `server.js` restart the server automatically.
- `GET /` → HTML page with heading "Base Code E2E".
- `GET /health` → `{"status":"ok"}`.

## Verification
- `curl http://localhost:3000/health` should return `{"status":"ok"}`.
- `curl http://localhost:3000/` should return HTML containing `Base Code E2E`.

## No secrets required
The app has no external service dependencies.
