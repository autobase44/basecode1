# Base Code E2E — Base44 Setup Notes

## Overview
Minimal zero-dependency Node.js HTTP server (`server.js`). No database, no external services, no environment variables required.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d --build`
- The app listens on port 3000 inside the container (`PORT=3000`).
- `GET /` returns the fixture HTML page; `GET /health` returns `{"status":"ok"}`.
- Source is bind-mounted; `nodemon` watches for file changes and restarts automatically.

## Verification
- `curl http://localhost:3000/` → HTML with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- The README warns not to change the app content — the E2E tests depend on it.
- No secrets or external credentials are needed.
