# Base44 Setup Notes

## Project
Minimal Node.js app (no dependencies, no database, no external services). Single `server.js` using Node's built-in `http` module. Serves a page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with source bind-mounted and `node --watch server.js` for live reload on file changes.
- No secrets or environment variables required.

## Verification
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E".

## Notes
- The README warns not to change the app files — tests depend on exact content. Only Base44 artifacts (compose, environment.json, this file) were added.
