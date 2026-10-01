# Base44 Dev Environment

## Overview
Minimal stateless Node.js HTTP server (`server.js`) — no dependencies, no database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted into the container; there is no live-reload dev server (plain `node server.js`), so call `reload_preview` after edits.
- `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Notes
- This repo is a fixture for Base44 Base Code E2E tests; do not change its content beyond Base44 setup artifacts.
- No secrets are needed.
