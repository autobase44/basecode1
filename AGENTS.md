# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Dev compose uses `node:20` with the source bind-mounted and `node --watch server.js` for live reload.
- Web entry point on host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Notes
- No `npm install` needed — the app has zero dependencies.
- No secrets or environment variables required.
- The repo is a test fixture; do not change its content (tests depend on it).
