# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with source bind-mounted at `/app`
- Runs `node --watch server.js` for live reload on file changes
- Port 3000 mapped to host
- Healthcheck probes `GET /health`

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- No `npm install` needed — zero dependencies, uses only `node:http`
- No external credentials required
