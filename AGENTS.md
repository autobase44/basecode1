# Base44 Setup Notes

## Project
Minimal Node.js web app (no dependencies, no database, no external services). A single `server.js` uses the built-in `http` module to serve an HTML page on port 3000 and a JSON `/health` endpoint.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- The app binds port 3000. Health check: `GET /health` → `{"status":"ok"}`.
- No live-reload dev server (plain `node server.js`); call `reload_preview` after source edits.

## Notes
- Do not modify `server.js`, `package.json`, or `README.md` — the repo is an E2E test fixture whose tests depend on exact content.
- No secrets or environment variables are required.
