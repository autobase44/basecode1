# Base Code E2E — Base44 notes

Minimal Node.js HTTP server (`server.js`), zero dependencies, zero env vars, no database.
Serves `GET /` (HTML page) and `GET /health` (`{"status":"ok"}`) on port 3000.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Source is bind-mounted; the app runs `node server.js` directly (no live-reload dev server — call `reload_preview` after edits).
- Healthcheck probes `http://localhost:3000/health`.

## Constraints
- README says the fixture's content is depended on by E2E tests — do not change `server.js` or `package.json` content/behavior.
