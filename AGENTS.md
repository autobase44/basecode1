# Base44 Dev Environment

Minimal Node.js app (`server.js`) with zero dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Web entry on host port 3000; healthcheck at `/health`.
- Runs from bind-mounted source via `node server.js` (no live-reload watcher — call `reload_preview` after edits).

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` — do NOT use it for dev; the Base44 compose mounts the source instead.
- No secrets or environment variables required to boot.
