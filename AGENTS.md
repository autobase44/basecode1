# Base44 Dev Environment

## Overview
Minimal Node.js app (`server.js`) with zero dependencies, no environment variables, and no database. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Uses `node:20-alpine` base image with source bind-mounted at `/app` and `node --watch server.js` for live reload on file changes.
- No build step, no dependency installation, no migrations or seeds needed.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- Compose healthcheck probes `/health` via wget.

## Notes
- The README states tests depend on exact content — avoid changing `server.js` or `package.json` behavior.
- The server binds to `::` (IPv4+IPv6) so `localhost` healthchecks work inside the container.
