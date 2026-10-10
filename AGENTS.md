# AGENTS.md

## Overview
Minimal Node.js HTTP server (no framework, no dependencies, no database). Serves a single HTML page at `/` and a JSON health check at `/health`.

## Setup
- Runs via `docker compose -f docker-compose.base44.yml up -d --build`.
- The app uses Node 20's built-in `--watch` flag for live reload on file changes.
- No external services, no credentials, no environment variables beyond `PORT` (defaults to 3000).
- Bind-mounted from source — edits to `server.js` are picked up automatically by `node --watch`.

## Verification
- `curl http://localhost:3000/` returns HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
