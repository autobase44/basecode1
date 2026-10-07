# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs via `node --watch server.js` (built-in Node 20 file watcher) with source bind-mounted, so edits hot-reload without image rebuilds.
- Port 3000 is the web entry point.
- Healthcheck probes `GET /health` → `{"status":"ok"}`.

## No secrets required
No environment variables or external credentials are needed.
