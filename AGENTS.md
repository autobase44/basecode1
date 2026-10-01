# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services, and no environment variables beyond `PORT`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Base image: `node:20-alpine`; source is bind-mounted at `/app`.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits.

## Health
- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the HTML page with heading "Base Code E2E".

## Notes
- The app binds `::` (IPv4+IPv6), so `localhost` healthchecks work.
- README says don't change the app content — E2E tests depend on it.
