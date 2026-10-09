# Base44 sandbox notes

## What this app is
Dependency-free Node HTTP server (`server.js`). No database, no external services,
no environment variables required. `GET /` serves the "Base Code E2E" page and
`GET /health` returns `{"status":"ok"}`.

## Running it here
`docker compose -f docker-compose.base44.yml up -d --build` (see the compose file).

- The repo's own `Dockerfile` is NOT used in the sandbox: it COPYs the source into
  the image, which freezes the code. The Base44 compose runs `node:20-alpine` with
  the repo bind-mounted and starts `node --watch server.js` so edits reload the server.
- `server.js` listens without an explicit host, so it binds IPv4+IPv6 and is
  reachable through the preview proxy on host port 3000. There is no framework-level
  Host/Origin allowlist to configure.
- No `npm install` step is needed: `package.json` declares no dependencies.

## Verifying
- `curl -sS http://localhost:3000/health` → `{"status":"ok"}`
- `curl -sS http://localhost:3000/` → HTML containing `data-testid="e2e-marker"`.
- `docker compose -f docker-compose.base44.yml ps` should report the `web` service healthy.

## Important
`README.md` states the E2E tests depend on this app's exact content — do not change
`server.js` or the served page unless explicitly asked.
