# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted; `node --watch` restarts on file changes (no framework hot reload — use `reload_preview` after edits to refresh the iframe).
- `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Notes
- No environment variables, no secrets, no external services required.
- The app binds to all interfaces (`::`) so healthchecks via `localhost` work.
