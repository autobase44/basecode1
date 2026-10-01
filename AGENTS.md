# AGENTS.md

Minimal Node.js fixture app (no dependencies, no database, no env vars).

## Running
- `docker compose -f docker-compose.base44.yml up -d` — bind-mounts source and runs `node --watch server.js` on port 3000.
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}` — used by the compose healthcheck.

## Notes
- No `npm install` needed; the app uses only `node:http`.
- `node --watch` provides live reload on source edits.
- The repo's own `Dockerfile` bakes source via `COPY` — do not use it for dev; the compose file mounts source instead.
