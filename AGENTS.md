# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves HTML at `/`, JSON at `/health`.
- Uses `node --watch` for live reload on file changes.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No environment variables or secrets required.
- Do not modify app content — tests depend on exact output.
