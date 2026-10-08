# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a single HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host port 3000).
- Uses `node --watch` for live reload on file changes.
- No environment variables, database, or external credentials required.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
