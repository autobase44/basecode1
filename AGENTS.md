# Base44 setup notes

This is a minimal Node.js HTTP server (`server.js`) with no dependencies, no database, and no environment variables.

- **Run:** `docker compose -f docker-compose.base44.yml up -d` — binds the repo into a `node:20-alpine` container and runs `node server.js` on port 3000.
- **Health:** `GET /health` returns `{"status":"ok"}`; `GET /` serves the page with heading "Base Code E2E".
- **No live reload:** the app is a plain `http.createServer` with no watcher; after editing `server.js`, call `reload_preview` (or restart the `web` service) so the change takes effect.
- **No secrets required.**
