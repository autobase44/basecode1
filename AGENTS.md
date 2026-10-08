# Base44 sandbox notes

This repo is a fixture (see README) — do not change `server.js`, `package.json` or the
`Dockerfile`; the E2E tests depend on their exact content.

## Running it here

- `docker compose -f docker-compose.base44.yml up -d --build`
- Service `web` runs `node --watch server.js` from the bind-mounted working copy, so edits
  to `server.js` reload without an image rebuild. The repo's own `Dockerfile` bakes the
  source in (`COPY ...`) and must NOT be used for the dev environment.
- No dependencies to install, no database, no environment variables, no secrets.
- Port 3000 is the single entry point.

## Verifying

- `curl -s localhost:3000/health` → `{"status":"ok"}`
- `curl -s localhost:3000/` → page containing `<h1 ...>Base Code E2E</h1>`
- The compose healthcheck probes `/health` via Node's global `fetch`.
