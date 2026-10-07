# Base44 Dev Environment

## Overview
Minimal Node.js app (no dependencies, no database, no external services). Single `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. Healthcheck: `GET /health` → `{"status":"ok"}`.

## Notes
- No secrets or external credentials required.
- Source is bind-mounted; restart the container to pick up `server.js` changes (no live-reload dev server — this is a plain `node` process).
