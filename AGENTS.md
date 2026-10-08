# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
- `server.js` — single-file HTTP server serving `/` (HTML page) and `/health` (JSON).
- Entry point: `npm start` → `node server.js`.

## Running in the Base44 sandbox
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- Source is bind-mounted, so edits are reflected without rebuilding the image.
- Healthcheck probes `GET /health` which returns `{"status":"ok"}`.

## No secrets required
The app has no environment variables beyond `PORT` (set in compose) and no external service credentials.
