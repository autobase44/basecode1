# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables beyond `PORT`. Serves a static HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- App runs on port 3000 via `node --watch server.js` (live reload on file changes).
- Source is bind-mounted; edits appear without rebuild.
- Healthcheck probes `http://localhost:3000/health`.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No secrets, no external services, no migrations or seeds needed.
- No package manager dependencies (`package.json` has no `dependencies`).
