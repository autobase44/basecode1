# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Used as a Base44 Base Code E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- Source is bind-mounted, so edits are reflected without rebuilding the image.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Notes
- The server binds `::` (IPv4+IPv6) so `localhost` healthchecks work.
- No secrets or external credentials required.
- No `npm install` needed — the app uses only `node:http`.
