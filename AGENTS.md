# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App served on port 3000; health check at `GET /health` → `{"status":"ok"}`.
- Uses `node --watch` for live reload on file changes.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No secrets or environment variables required beyond `PORT` (defaults to 3000).
- No package dependencies to install — `package.json` has none.
