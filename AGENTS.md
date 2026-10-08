# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no environment variables, and no database. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted into the container, but there is no live-reload dev server (plain `node server.js`). After editing `server.js`, call `reload_preview` or restart the service for changes to appear.

## Health Check
- `GET /health` returns `{"status":"ok"}`.

## Secrets
- None required.
