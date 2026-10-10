# AGENTS.md

## Setup
- Minimal Node.js app (no dependencies, no database, no external services).
- Runs via `docker compose -f docker-compose.base44.yml up -d` — uses `node:20-alpine` with source bind-mounted and `node --watch server.js` for live reload.
- No secrets or environment variables required.
- Health check: `GET /health` returns `{"status":"ok"}`.
- Web entry point on port 3000: `GET /` shows the "Base Code E2E" page.

## Notes
- The README says not to change the app — tests depend on its exact content.
- `server.js` binds to `::` (IPv4+IPv6), so `localhost` healthchecks work.
