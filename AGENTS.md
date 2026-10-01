# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables required. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 (mapped from container port 3000).
- Uses `node --watch server.js` for live reload on file changes — no rebuild needed after edits.
- Base image: `node:20-alpine`; source is bind-mounted at `/app`.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
