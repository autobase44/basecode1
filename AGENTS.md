# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no env vars, no database.
Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs from bind-mounted source on `node:20-alpine` with `node --watch` for live reload.
- Port 3000 is the web entry point.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Notes
- No `npm install` needed — the app uses only `node:http` (built-in).
- No external credentials required.
- The server binds `::` (all interfaces), so it accepts external hostnames out of the box.
