# AGENTS.md

## Running the app here

- Run with `docker compose -f docker-compose.base44.yml up -d --build`.
- `docker-compose.base44.yml` runs `node --watch server.js` from the bind-mounted
  repo root, so edits to `server.js` restart the server automatically. It does NOT
  use the repo's own `Dockerfile` (that bakes the source into an image and would
  freeze edits).
- The app is a single dependency-free Node HTTP server: no `npm install`, no
  database, no migrations, no environment variables or secrets required.
- `server.js` listens without a host argument, so it binds both IPv4 and IPv6 —
  `localhost` and `127.0.0.1` both work.

## Verifying it works

- `GET /` -> HTML page with heading `Base Code E2E` (`data-testid="e2e-marker"`).
- `GET /health` -> `{"status":"ok"}` (also used by the compose healthcheck).

## Notes

- This repo is an E2E test fixture; the README asks not to change its content
  (heading text, `/health` response). Keep app behavior as-is.
