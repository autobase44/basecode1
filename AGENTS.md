# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes.
- Health check: `GET /health` returns `{"status":"ok"}`.
- The server binds `::` (all interfaces), so it accepts the preview proxy's external hostname.

## Verification
- `curl http://localhost:3000/` — should return HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` — should return `{"status":"ok"}`.
