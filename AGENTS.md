# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database.
Serves a single HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (configurable via `PORT` env, defaults to 3000).
- No environment variables or secrets required.
- No external services or credentials needed.

## Live reload
Uses Node's built-in `--watch` flag (Node 20+) for automatic restart on file changes.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
