# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch` (Node 20+ built-in) for live reload on file changes.
- No database, no external services, no environment variables or secrets required.

## Verification
- `curl http://localhost:3000/` returns HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
