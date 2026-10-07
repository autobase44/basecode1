# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with source bind-mounted at `/app`.
- Runs `node --watch server.js` for live reload on file changes.
- Port 3000 mapped to host.

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## No secrets required
The app needs no environment variables or external credentials.
