# AGENTS.md

## Project: base-code-e2e

Minimal zero-dependency Node.js HTTP server (`server.js`) used as a Base44 test fixture.

- **No npm dependencies** — `package.json` has none; `npm install` is unnecessary.
- **No database, no external services, no secrets.**
- **Run:** `docker compose -f docker-compose.base44.yml up -d` — serves on port 3000.
- **Live reload:** uses `node --watch server.js`; edits to `server.js` restart the server automatically.
- **Health check:** `GET /health` returns `{"status":"ok"}`.
- **Verify:** `curl http://localhost:3000/` should return HTML with heading "Base Code E2E".
