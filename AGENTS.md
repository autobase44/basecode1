# AGENTS.md

## What this is
Minimal, dependency-free Node HTTP server (`server.js`). No `npm install`, no
build step, no database, no environment variables.

## Running it (Base44 sandbox)
`docker compose -f docker-compose.base44.yml up -d`

- The stack runs `node --watch server.js` from the bind-mounted checkout on host
  port 3000, so source edits restart the server automatically.
- `PORT=3000` is passed by the compose file; `server.js` defaults to 3000 anyway.
- Do not use the repo's own `Dockerfile` for the preview: it `COPY`s the source
  into an image, which would hide live edits.

## Verifying
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}` (the compose healthcheck).

## Note
This repo is a fixture for Base44 E2E tests; the page content is asserted by
those tests, so avoid changing it.
