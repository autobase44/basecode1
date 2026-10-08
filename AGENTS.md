# AGENTS.md

## Project

Minimal zero-dependency Node.js HTTP server (`server.js`) used as a Base44 E2E test fixture.

- No npm dependencies, no environment variables, no database.
- `npm start` runs `node server.js` on port 3000.
- `GET /` serves an HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Running in the sandbox

- `docker compose -f docker-compose.base44.yml up -d --build`
- Uses `node --watch` for live reload (built into Node 20, no extra dependency needed).
- Source is bind-mounted; edits to `server.js` auto-restart the server.
- Healthcheck probes `GET /health`.

## Verification

- `curl http://localhost:3000/` → HTML page with "Base Code E2E" heading.
- `curl http://localhost:3000/health` → `{"status":"ok"}`.
