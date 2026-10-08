# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs from bind-mounted source using `node --watch server.js` (live reload on file changes).
- Web entry point: port 3000 → `GET /` (HTML page), `GET /health` (JSON `{"status":"ok"}`).

## Verification
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
- The page heading is "Base Code E2E".

## Notes
- No secrets or environment variables are required.
- No package installation step needed — the app uses only `node:http`.
