# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, bound to `0.0.0.0`.
- Uses `node --watch` for live reload on file changes (no extra dependencies needed).
- No database, no external services, no secrets required.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
