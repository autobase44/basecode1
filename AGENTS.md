# Base44 Setup Notes

## Project
Minimal Node.js test-fixture app (`base-code-e2e`). Single file `server.js` — no dependencies, no database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` base image with source bind-mounted at `/app`.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after edits.
- Health check: `GET /health` returns `{"status":"ok"}`.
- Main page: `GET /` returns HTML with heading "Base Code E2E".

## Constraints
- README says: don't change the app content — tests depend on it.
- No secrets needed.
