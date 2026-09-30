# Base44 Setup Notes

This is a minimal Node.js web app (no dependencies, no database, no env vars).

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The compose uses `node:20-alpine` with the source bind-mounted at `/app` and runs `node --watch server.js` for live reload on edits.
- No `npm install` needed — the app uses only Node built-ins (`node:http`).

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Healthcheck in compose probes `/health` via wget.

## Constraints
- The README says: do not change the app's content — E2E tests depend on its exact output.
