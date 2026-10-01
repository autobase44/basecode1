# Base44 Dev Environment

## Overview
Minimal zero-dependency Node.js HTTP app (`server.js`) used as an E2E fixture.
- No `npm` dependencies, no database, no required environment variables.
- `GET /` serves an HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with the repo bind-mounted at `/app`.
- Runs `node --watch server.js` (Node's built-in file watcher) for live reload on edits.
- Web entry point on host port 3000.
- Healthcheck probes `http://localhost:3000/health`.

## Verifying
```
curl http://localhost:3000/health   # -> {"status":"ok"}
curl http://localhost:3000/         # -> HTML page with "Base Code E2E"
```
