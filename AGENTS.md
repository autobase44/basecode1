# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables. Serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- App runs from bind-mounted source via `node --watch` (live reload on file changes).
- Port 3000 is the web entry point.
- Healthcheck probes `GET /health` → `{"status":"ok"}`.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No external credentials or secrets required.
- The server binds to `::` (all interfaces) — no host allowlist needed.
