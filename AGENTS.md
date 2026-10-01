# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — runs `node --watch server.js` from a bind-mounted `node:20-alpine` image (live reload on file change).
- Web entry point: host port 3000.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Notes
- Repo root is `/app` in the sandbox.
- No external services or credentials required.
