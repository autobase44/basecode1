# Base44 sandbox notes

## Running it here
- `docker compose -f docker-compose.base44.yml up -d` — the only supported way to run this app in the sandbox.
- The compose stack does **not** use the repo's `Dockerfile`. That Dockerfile COPYs the source into an image at build time, so any edit to `server.js` would be invisible in the preview. The compose service instead bind-mounts the repo at `/app` and runs `node --watch server.js`, so editing `server.js` restarts the server in place.
- No `npm install` step exists or is needed: `package.json` declares no dependencies, and there is no lockfile.

## Verifying it works
- `curl -s http://localhost:3000/` should return the page containing `data-testid="e2e-marker"` and the heading `Base Code E2E`.
- `curl -s http://localhost:3000/health` should return `{"status":"ok"}`.
- There are no tests, no database, and no migrations to run.

## Quirks
- The app has no environment variables and no secrets; nothing needs to be configured to boot it.
- `server.js` calls `.listen(PORT)` with no host argument on purpose — that binds both IPv4 and IPv6 so a `localhost` healthcheck resolves.
- This repo is an E2E test fixture and its README asks that its content stay exactly as-is; the page markup, `/health` response and heading are asserted verbatim by those tests.
