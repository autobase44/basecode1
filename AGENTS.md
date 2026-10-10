# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Serves a static page at `/` with heading "Base Code E2E" and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs from bind-mounted source with `node --watch` for live reload.
- Port 3000 maps to the container's port 3000.
- No environment variables or secrets required.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with "Base Code E2E" heading.

## Notes
- The README says tests depend on exact content — do not modify `server.js` or `package.json`.
