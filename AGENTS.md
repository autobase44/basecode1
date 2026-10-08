# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Run
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. Health check at `GET /health` returns `{"status":"ok"}`.

## Live reload
Uses Node's built-in `--watch` mode — edits to `server.js` restart the server automatically.

## No secrets required
The app needs no external credentials.
