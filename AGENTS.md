# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no framework, no dependencies, no database). Serves a static HTML page at `/` and a JSON health check at `/health`.

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted; `server.js` runs directly with `node` (no live-reload dev server — use `reload_preview` after edits).
- No environment variables or external credentials are required.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
