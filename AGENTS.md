# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with source bind-mounted at `/app`.
- Runs `node --watch server.js` for live reload on file changes.
- Web entry point on host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## No secrets required
The app has no environment variables, no database, and no external service dependencies.
