# Base44 Dev Environment

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Runs from bind-mounted source with `node --watch` for live reload.
- No secrets or environment variables required.

## Verify
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
