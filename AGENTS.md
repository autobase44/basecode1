# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, binds all interfaces (`::`).
- Live reload via Node's built-in `--watch` flag — edits to `server.js` restart the server automatically.

## Health Check
- `GET /health` returns `{"status":"ok"}`.

## Notes
- The README asks not to change app content — E2E tests depend on exact output.
- No secrets or external credentials required.
