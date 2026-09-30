# Base44 Dev Notes

Minimal zero-dependency Node HTTP server (`server.js`) serving a static HTML page and `/health`.

- No package dependencies, no env vars, no database.
- Dev compose (`docker-compose.base44.yml`) uses `node:20-alpine` with the source bind-mounted and runs `node --watch server.js` for live reload on edits.
- Healthcheck hits `GET /health` → `{"status":"ok"}`.
- The repo's own `Dockerfile` is a production build (copies source) — not used for dev; edits must be visible via the bind mount.
