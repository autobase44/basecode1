# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services. Single file serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs via `node --watch server.js` (Node 20 built-in file watcher) with source bind-mounted, so edits hot-reload without rebuilds.
- Web entry point on host port 3000.

## Verification
- `GET /health` → `{"status":"ok"}`
- `GET /` → HTML page with heading "Base Code E2E"

## Notes
- No secrets or environment variables required.
- The README and tests depend on exact content — do not change the app's output.
