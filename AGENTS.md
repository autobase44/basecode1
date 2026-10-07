# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external credentials.
Serves a static HTML page at `/` and `{"status":"ok"}` at `/health`.

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Runs from cloned source via bind-mount with `nodemon` for live reload on `server.js` changes.
- Base image: `node:20-alpine`; nodemon installed at container startup.
- Healthcheck probes `http://localhost:3000/health`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- This is a test fixture; the README asks not to change its content.
- No secrets or environment variables are required to boot.
