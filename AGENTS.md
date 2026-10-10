# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database. Serves a static page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000.
- Uses `node --watch` for live reload on file changes (Node 20+ built-in).
- No environment variables, secrets, or external services required.

## Verification
- `curl http://localhost:3000/` returns HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
