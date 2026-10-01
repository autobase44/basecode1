# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.
- `npm start` runs `node server.js`, serving `GET /` (HTML page) and `GET /health` (JSON).
- Listens on port 3000 (configurable via `PORT` env var), binds all interfaces.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app with `node --watch` for live reload.
- Source is bind-mounted at `/app`; edits to `server.js` trigger automatic restart.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## No secrets required
No environment variables or external credentials are needed.
