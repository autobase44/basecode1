# AGENTS.md

Notes for agents working in this repo inside the Base44 sandbox.

## Running it here

- Use the Base44 compose, not the repo `Dockerfile`:
  `docker compose -f docker-compose.base44.yml up -d --build`
- `docker-compose.base44.yml` runs `node --watch server.js` from the bind-mounted
  source on `node:22-alpine`. The repo's own `Dockerfile` copies the source into a
  prebuilt image, so edits would never show up in the preview — don't use it for
  the sandbox.
- The app is a single dependency-free file (`server.js`); there is nothing to
  install, no database, and no environment variables are required.
- `BASE44_PREVIEW_MODE` is passed through to the service bare. Nothing in this app
  currently reads it.
- Web entry point: host port 3000, health endpoint `GET /health` → `{"status":"ok"}`.

## Verifying

- `curl -sf http://localhost:3000/health` → `{"status":"ok"}`
- `curl -s http://localhost:3000/ | grep 'Base Code E2E'`

## Caveat

The README asks that the app's content not be changed: it is an E2E test fixture.
Keep app code as-is; Base44 setup files are additive only.
