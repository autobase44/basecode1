# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
App is served on host port 3000.

## Notes
- No live-reload dev server exists (plain `node server.js`); call `reload_preview` after source edits.
- No external credentials required.
- Healthcheck probes `GET /health` which returns `{"status":"ok"}`.
