# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the repo bind-mounted at `/app`; source edits require a `reload_preview` (no live-reload dev server).
- Healthcheck probes `http://localhost:3000/health`.

## Verifying
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".

## Notes
- No external credentials or secrets needed.
- This is an E2E test fixture; the tests depend on its exact content.
