# Base44 dev environment notes

Minimal zero-dependency Node.js app (plain `node:http`, no framework, no DB, no env vars, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted; the app runs `node server.js` directly (no build step, no live-reload dev server — call `reload_preview` after edits, or `docker compose restart web`).
- `GET /` returns the HTML page; `GET /health` returns `{"status":"ok"}` (used by the compose healthcheck).
- No secrets required.
