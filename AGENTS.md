# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file: `server.js` — serves `GET /` (HTML page) and `GET /health` (JSON).

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (configurable via `PORT` env var, defaults to 3000).
- Live reload via `node --watch` (Node 20 built-in) — edits to `server.js` restart automatically.

## Verification
- `GET /` returns HTML with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## No Secrets Required
No environment variables or external credentials are needed to run this app.
