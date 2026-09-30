# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no env vars.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted; `nodemon` watches `server.js` for live reload.
- Health check: `GET /health` → `{"status":"ok"}`.
- No secrets required.
