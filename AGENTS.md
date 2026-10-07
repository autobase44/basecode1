# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services. Serves a static HTML page at `/` and a JSON health check at `/health` on port 3000.

## Running in Base44
- `docker compose -f docker-compose.base44.yml up -d` starts the app from source using `node --watch` (Node 20 built-in file watcher) for live reload.
- No secrets, no environment variables beyond `PORT` (defaults to 3000).
- Health check: `curl http://localhost:3000/health` → `{"status":"ok"}`.

## Notes
- The README says not to change app content — E2E tests depend on exact output.
- `server.js` binds to `::` (all interfaces), so it's reachable from the preview proxy without host allowlist configuration.
