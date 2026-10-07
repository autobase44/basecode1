# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d --build` starts the app on port 3000.
- The container bind-mounts the repo at `/app` and runs `node server.js` directly (no live-reload framework — call `reload_preview` after source edits).
- Health check: `GET /health` returns `{"status":"ok"}`.

## Notes
- The README says not to change this fixture app; tests depend on its exact content.
- No external credentials or secrets are needed.
