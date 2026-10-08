# Base44 Setup Notes

## Overview
Minimal zero-dependency Node.js HTTP server (`server.js`) serving a static HTML page and a `/health` JSON endpoint on port 3000.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app.
- No dependencies to install (`package.json` has none).
- No database, no secrets, no environment variables required.
- The app has no live-reload dev server (plain `node server.js`); call `reload_preview` after code changes.

## Health Check
- `GET /health` returns `{"status":"ok"}`.
- Compose healthcheck uses `wget` against `http://localhost:3000/health`.

## Notes
- The README warns not to change this fixture app — E2E tests depend on its exact content.
