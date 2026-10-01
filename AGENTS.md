# Base44 Dev Environment

Minimal Node.js app (`server.js`) — no dependencies, no database, no env vars.

## Run
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000; `GET /` serves the page, `GET /health` returns `{"status":"ok"}`.
- Live reload via Node's built-in `--watch` (no nodemon needed). Edits to `server.js` restart the server automatically.

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` (production build) — do NOT use it for dev; the Base44 compose bind-mounts the source instead.
- No external credentials required.
