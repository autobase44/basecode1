# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Setup
- Runtime: `node:20-alpine` via `docker-compose.base44.yml`
- Source is bind-mounted at `/app` inside the container; edits are visible immediately
- No live-reload dev server (plain `node server.js`) — call `reload_preview` after code changes
- No environment variables or secrets required
- Start: `docker compose -f docker-compose.base44.yml up -d`

## Verification
- `GET /` returns the page with heading "Base Code E2E"
- `GET /health` returns `{"status":"ok"}`
- Container healthcheck probes `/health` via wget
