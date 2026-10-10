# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with **no dependencies**, **no environment variables**, and **no database**. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` brings up the app on port 3000.
- The source is bind-mounted; there is no live-reload dev server (plain `node server.js`). After editing `server.js`, call `reload_preview` or restart the container for changes to appear.

## Verification
- `GET /` returns HTML with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Constraints
- The README asks not to change app files — tests depend on exact content.
