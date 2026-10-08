# Notes for agents

## Do not change `server.js` / `README.md` content on purpose
This repo is a fixture for Base44 Base Code E2E tests; the tests assert the exact
heading text `Base Code E2E` (`data-testid="e2e-marker"`) and the `/health` JSON.
Keep changes minimal.

## Running it here
`docker compose -f docker-compose.base44.yml up -d --build` — a single `web` service
on host port 3000. The service runs `node --watch server.js` directly from the
bind-mounted checkout (no install step: the project has no dependencies, lockfile,
env vars or database). Do not use the repo `Dockerfile` for the sandbox: it bakes the
source into the image, so edits would not show up.

## Verifying
- `curl -s localhost:3000/` contains `Base Code E2E`.
- `curl -s localhost:3000/health` returns `{"status":"ok"}`.
- `node --watch` restarts on edit to `server.js`, so no manual restart is needed.
