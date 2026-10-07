# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables, and no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch` (Node 20+ built-in) for live reload on file changes — no extra dependency needed.
- Source is bind-mounted from the repo root; edits to `server.js` trigger an automatic restart.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Healthcheck in compose probes `/health`.

## Notes
- The repo's own `Dockerfile` copies source in (production-style); the Base44 compose instead bind-mounts and uses `node --watch` so edits are live without rebuilds.
- No secrets or external credentials are required.
