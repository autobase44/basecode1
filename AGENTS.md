# Base44 Dev Environment

Minimal Node.js http server (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted; `node --watch server.js` provides live reload on file changes.
- No secrets or environment variables required.

## Verifying
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
