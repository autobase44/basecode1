# Base44 Setup Notes

This is a minimal Node.js app (`server.js`) — no dependencies, no database, no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes.
- Base image: `node:20-alpine`; source is bind-mounted at `/app`.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}`.

## Notes
- The README warns not to change the app content — E2E tests depend on it.
- No secrets or external credentials required.
