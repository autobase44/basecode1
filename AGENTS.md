# Base44 Dev Environment

## Project
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Runs from bind-mounted source with `node --watch server.js` (Node 20 built-in live reload).
- No secrets or environment variables required.

## Verify
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
