# AGENTS.md

## Running this project in the Base44 sandbox

- Start with: `docker compose -f docker-compose.base44.yml up -d --build`
- The app is a dependency-free Node HTTP server (`server.js`). There is no
  package install step, no environment variables and no database.
- `docker-compose.base44.yml` runs the app from the bind-mounted repo source
  using a plain `node:22-alpine` image. Do NOT use the repo's own `Dockerfile`
  to run it here: it `COPY`s the source into the image, which would hide edits.
- There is no live-reload dev server (the app is a plain `node server.js`).
  After editing source, restart the service and call `reload_preview`:
  `docker compose -f docker-compose.base44.yml restart web`

## Verifying it works

- `GET /` renders a page with the heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}` (used by the Compose healthcheck).
- Quick check: `curl -fsS http://localhost:3000/health`

## Notes

- The repo is an E2E test fixture; its content (heading, routes) is asserted by
  tests, so avoid changing the app's own output.
