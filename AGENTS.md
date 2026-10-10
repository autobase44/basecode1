# Base44 Dev Environment

## Project
Minimal zero-dependency Node.js HTTP server (`server.js`). No npm packages, no database, no environment variables, no external services.

## Setup
- `docker compose -f docker-compose.base44.yml up -d --build` brings up the app on port 3000.
- The compose uses `node:20` with the source bind-mounted at `/app` and `node --watch server.js` for live reload on edits.
- No secrets or credentials are required.

## Verification
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Healthcheck in compose probes `/health` via `node -e fetch(...)`.

## Notes
- The README says: do not change the app content — E2E tests depend on exact output.
- Node 20+ built-in `--watch` mode provides live reload without any extra dependency.
