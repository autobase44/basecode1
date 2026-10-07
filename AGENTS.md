# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. No database, no external services, no environment variables required.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on edits to `server.js`.
- Source is bind-mounted, so edits appear without rebuilding the image.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Verification
- `curl http://localhost:3000/` returns the page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.

## Notes
- The README states the tests depend on the exact content — do not change the page text or health endpoint.
