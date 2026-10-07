# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no environment variables, and no database. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` base image with the repo bind-mounted at `/app`.
- No live-reload dev server; after editing `server.js`, restart the service:
  `docker compose -f docker-compose.base44.yml restart web`
- Web entry point on host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Constraints
- The README states the test fixture content must not be changed — the E2E tests depend on exact page content (heading "Base Code E2E").
