# AGENTS.md

## Project overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no external services). Serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 inside the container (`PORT` env var, defaults to 3000).
- No dependencies to install — `server.js` uses only `node:http`.

## Live reload
This is a plain `node` HTTP server with no file watcher. After editing `server.js`, call `reload_preview` (or restart the `web` service) for changes to appear.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- The README says not to change the app content — the E2E test fixture depends on its exact text.
- No secrets or external credentials are needed.
