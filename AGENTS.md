# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The container uses `node:20-alpine` with the source bind-mounted at `/app` and `node --watch server.js` for live reload on file changes.

## Verification
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
