# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no external services. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- App listens on port 3000 (mapped to host 3000).
- Uses `node --watch` for live reload on file changes.
- Source is bind-mounted from the repo root into `/app`; edits appear without rebuilding.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No environment variables, secrets, or migrations required.
- Node >= 20 required (uses `node --watch`).
