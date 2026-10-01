# Base44 Dev Environment

## Overview
Minimal Node.js app (`server.js`) — a static HTML page + `/health` JSON endpoint.
No dependencies, no environment variables, no database.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Web service: `node:20-alpine` with source bind-mounted at `/app`, runs `node --watch server.js` for live reload on edits.
- Port 3000 is the user-facing entry point.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Verification
- `GET /` shows the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
