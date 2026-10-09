# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
- `server.js` — plain `http.createServer` serving a static HTML page at `/` and JSON at `/health`.
- No build step, no live-reload dev server. Changes require `reload_preview` or container restart.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with source bind-mounted at `/app`.
- Port 3000 mapped to host.
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Secrets
None required.
