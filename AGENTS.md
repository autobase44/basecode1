# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (single file `server.js`, zero dependencies).
No database, no external services, no environment variables required.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with source bind-mounted at `/app`.
- Dev command: `node --watch server.js` (built-in live reload on file changes).
- Port 3000 mapped to host.

## Health
- `GET /health` → `{"status":"ok"}`
- `GET /` → HTML page with heading "Base Code E2E"

## Notes
- The server binds to `::` (all interfaces) so it's reachable from the preview proxy.
- No secrets or credentials needed.
