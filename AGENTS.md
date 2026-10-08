# AGENTS.md

## Running the app (Base44 sandbox)

- `docker compose -f docker-compose.base44.yml up -d --build` — starts the whole stack.
- The app is a single zero-dependency Node HTTP server (`server.js`). There is no
  database, no environment variables, and no external services, so no secrets are needed.
- The repo's own `Dockerfile` bakes the source (`COPY package.json server.js ./`) into a
  production image, so it can't reflect edits. `docker-compose.base44.yml` instead runs
  `node:20-alpine` with the repo bind-mounted at `/app` and `node --watch server.js` for
  live reload. Edit `server.js` and the container restarts automatically.
- Health: `GET /health` returns `{"status":"ok"}`. The `web` service healthcheck probes it.
- `GET /` serves the fixture page (heading "Base Code E2E", `data-testid="e2e-marker"`).

This repo is a fixture for Base44 end-to-end tests — do not change `server.js` content.
