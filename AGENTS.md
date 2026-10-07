# Base44 Setup Notes

## Project

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running

- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host 3000).
- Uses `node --watch` (Node 20+ built-in) for live reload on file changes — no nodemon dependency needed.
- Source is bind-mounted at `/app`; edits appear after the watcher restarts the process.

## Verification

- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes

- No external credentials or secrets required.
- No migrations or seeds.
- The repo's own `Dockerfile` builds a production image (copies source in); the Base44 compose uses a plain `node:20-alpine` base with a bind mount instead so edits are live.
