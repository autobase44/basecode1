# Base44 Dev Environment

## App overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: http://localhost:3000
- Health check: http://localhost:3000/health → `{"status":"ok"}`

## Notes
- No live-reload dev server; the app runs via plain `node server.js`. After editing `server.js`, call `reload_preview` (or `docker compose restart web`) to see changes.
- No secrets or external services required.
- The repo is a test fixture — avoid changing `server.js` or `package.json` content beyond what a task requires; E2E tests depend on their exact content.
