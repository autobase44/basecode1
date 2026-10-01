# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs on port 3000 with `node --watch server.js` (live reload on file changes).
- Source is bind-mounted; no image rebuild needed for edits.
- Health check: `GET /health` → `{"status":"ok"}`

## Notes
- No `npm install` needed — the app uses only `node:http`.
- No secrets or external services required.
