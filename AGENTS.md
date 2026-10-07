# AGENTS.md

Minimal Node.js fixture app (`server.js`, no dependencies, no database, no env vars).

## Run
- `docker compose -f docker-compose.base44.yml up -d` — runs `node --watch server.js` from a bind-mount of the repo on `node:20-alpine`, port 3000.
- Node's built-in `--watch` provides live reload on edits (no nodemon needed).
- Health check: `GET /health` → `{"status":"ok"}`. Home page: `GET /` → HTML with heading "Base Code E2E".

## Notes
- No external credentials required. No secrets configured.
- The README warns the test suite depends on exact content — avoid changing `server.js` content.
