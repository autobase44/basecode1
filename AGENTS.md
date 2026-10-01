# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external credentials).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, bound to `0.0.0.0`.
- Source is bind-mounted at `/app`; restart the container after edits (no live-reload dev server — plain `node server.js`).

## Health
- `GET /health` returns `{"status":"ok"}`.
