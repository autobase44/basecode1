# Project notes for automated/dev setup

This is a minimal fixture app (plain Node `http` server, no framework).

## Running it here

- `docker compose -f docker-compose.base44.yml up -d --build` — single service `app` on Node 20,
  bind-mounting the repo at `/app` and running `node --watch server.js` (live reload on file change).
- Public entry point: host port **3000** (`PORT=3000` passed in Compose).
- Healthcheck probes the app's own real endpoint: `wget --spider http://127.0.0.1:3000/health`
  (busybox wget ships with the alpine image; no extra tooling added).

## Non-obvious things

- **No dependencies, no lockfile, no database, no environment variables.** There is nothing to
  `npm install` and nothing to migrate/seed — the Compose file deliberately has no install step.
- **Do not edit `server.js` content.** The README states this app is a fixture for Base44 Base Code
  E2E tests and that the tests depend on its exact content (`GET /` heading "Base Code E2E",
  `GET /health` → `{"status":"ok"}`).
- The server calls `listen(PORT)` without a host, binding both IPv4 and IPv6, so `localhost`
  healthchecks work.

## How to verify

```sh
curl -sS http://localhost:3000/        # HTML page with heading "Base Code E2E"
curl -sS http://localhost:3000/health  # {"status":"ok"}
```
