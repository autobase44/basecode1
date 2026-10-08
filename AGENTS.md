# Base Code E2E — Dev Notes

Minimal Node.js HTTP server (no dependencies, no database, no external services).

## Running locally
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes.
- Health check: `GET /health` returns `{"status":"ok"}`.
- No environment variables or secrets required.

## Verifying
- `curl http://localhost:3000/` — should return the page with heading "Base Code E2E".
- `curl http://localhost:3000/health` — should return `{"status":"ok"}`.
