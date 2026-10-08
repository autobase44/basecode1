# AGENTS.md

Guidance for AI agents working in this repository in the Base44 sandbox.

## Running the app here

- Use `docker-compose.base44.yml` (NOT the repo's own `Dockerfile`, which bakes
  the source into a prebuilt image and would freeze the edit loop):
  `docker compose -f docker-compose.base44.yml up -d --build`
- Serve URL: http://localhost:3000 (web entry point, host port 3000).
- Verification: `GET /` returns the "Base Code E2E" page; `GET /health` returns
  `{"status":"ok"}`.

## Notes / quirks

- Zero runtime dependencies and no lockfile — there is no install step. If a
  dependency is ever added, add a lockfile-preserving `npm ci` (or `npm install`)
  to the service `command` before `node --watch server.js`.
- The app is a single `server.js` with no framework and no watcher built in;
  the Base44 compose runs it under `node --watch` so source edits reload live.
- No database, no migrations, no seeds, no environment variables required, and no
  external-service credentials needed.
- `server.js` listens without an explicit host, which binds all interfaces — the
  preview proxy can reach it.
