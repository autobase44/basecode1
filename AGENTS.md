# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`), no dependencies, no database, no external credentials.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App served on host port 3000; uses `node --watch` for live reload on edits.
- Health check: `GET /health` → `{"status":"ok"}`

## Notes
- No `npm install` needed — zero dependencies.
- The repo's own `Dockerfile` builds a production image (bakes source via COPY); do not use it for dev — the compose file runs from the bind-mounted source instead.
