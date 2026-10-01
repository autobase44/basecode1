# Base44 Agent Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file: `server.js`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves HTML at `/`, JSON at `/health`.
- Uses `node --watch server.js` for live reload on file changes.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## No Secrets Required
This app has no environment variables or external credentials.
