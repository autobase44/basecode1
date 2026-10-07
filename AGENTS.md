# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.
Serves a page at `/` and `{"status":"ok"}` at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- Web entry point: host port 3000.
- The container runs `node --watch server.js` (Node 20 built-in file watcher) with the repo bind-mounted at `/app`, so edits to `server.js` reload automatically.

## Healthcheck
- `GET /health` returns `{"status":"ok"}`.

## Secrets
- None required. The app has no environment variables beyond `PORT`.
