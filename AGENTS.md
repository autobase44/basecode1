# Base44 dev environment notes

This is a minimal Node fixture (`server.js`, no dependencies, no env vars, no database).

## Running it here
- `docker compose -f docker-compose.base44.yml up -d --build`
- The `app` service uses a plain `node:20-alpine` image with the repo bind-mounted at
  `/app` and runs `node --watch server.js`, so edits to `server.js` restart the server
  automatically (live reload, no rebuild needed).
- Web entry point: host port 3000. Healthcheck probes `GET /health` with Node's fetch.

## Quirks
- The repo's own `Dockerfile` bakes the source in via `COPY . .`, so it is NOT used for
  the sandbox — it would freeze the code. `docker-compose.base44.yml` is the runbook.
- `server.js` deliberately calls `listen(PORT)` without a host so it binds all
  interfaces (IPv4+IPv6); keep it that way for the preview proxy to reach it.
- Do not change the page content or the `e2e-marker` test id: Base44 E2E tests assert them.

## Verifying
- `curl -sf http://localhost:3000/health` -> `{"status":"ok"}`
- `curl -s http://localhost:3000/` -> page with heading `Base Code E2E`
