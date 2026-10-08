# AGENTS.md

## Running here

- `docker compose -f docker-compose.base44.yml up -d --build` starts the only service (`web`)
  on host port 3000, serving the cloned source from the repo bind-mount.
- The repo's own `Dockerfile` is NOT used for the sandbox: it bakes `server.js` into an image
  with `COPY`, so edits would not be visible. `docker-compose.base44.yml` runs `node:20-alpine`
  with the repo mounted at `/app` and `node --watch server.js` for reload on edit.
- `PORT=3000` is set in compose; `server.js` listens on all interfaces (`::`), so the container
  port mapping and the in-container `localhost` healthcheck both work.

## Things that are easy to get wrong

- No dependencies, no lockfile, no install step — do not add an `npm install` to the startup
  command, it would create a lockfile in the repo for nothing.
- No env vars or secrets are needed; nothing reads `/run/base44/app.env`.
- The app does not check `Host` or `Origin`, so no allowlist configuration is required for the
  preview proxy.

## Verifying it works

- `curl -s http://localhost:3000/health` → `{"status":"ok"}`
- `curl -s http://localhost:3000/` → HTML page whose `<h1 data-testid="e2e-marker">` reads
  `Base Code E2E`
