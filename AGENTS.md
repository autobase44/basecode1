# AGENTS.md

## Overview

Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running in Base44

- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch` for live reload on file changes (bind-mounted source).
- No dependencies to install, no environment variables, no database, no external credentials needed.

## Verification

- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
