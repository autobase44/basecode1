# Base44 Dev Environment

Minimal Node.js HTTP server (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000 with Node's built-in `--watch` for live reload.
- Source is bind-mounted at `/app`; edits to `server.js` auto-restart the server.
- Health check: `GET /health` → `{"status":"ok"}`.

## Notes
- No secrets or environment variables are required.
- The app binds `::` (dual-stack), so `localhost` healthchecks work.
