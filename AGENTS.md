# Base44 Setup Notes

## Project
Minimal Node.js web app (no dependencies, no database, no env vars). Single `server.js` using only `node:http`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App served on port 3000; `/health` returns `{"status":"ok"}`.
- Source is bind-mounted into a `node:20-alpine` container — edits to `server.js` require a container restart (no live-reload dev server; plain `node server.js`).

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- No secrets or external credentials needed.
- The repo's own `Dockerfile` bakes source via `COPY`; the Base44 compose uses a runtime image + bind mount instead so edits are visible without rebuilding.
