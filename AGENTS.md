# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables required. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch` (built into Node 20) for live reload on file changes.
- No build step, no migrations, no seeds.

## Verification
- `GET /` returns HTML with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Notes
- The README states this is a test fixture; do not change its content unless intentionally modifying the fixture.
