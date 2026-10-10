# Base44 setup notes

This repo is the `base-code-e2e` fixture: a single dependency-free Node HTTP server
(`server.js`). The repo README asks that its content not be changed — tests depend on
the exact page and `/health` response.

## Running here

- `docker-compose.base44.yml` runs the app from the cloned source: a plain `node:20-alpine`
  image with the repo bind-mounted at `/app` and `node --watch server.js` for live reload.
- No `npm install` is needed (no dependencies, no lockfile). Do not run `npm install`, as it
  would add an unrelated `package-lock.json`.
- `GET /` serves the page; `GET /health` returns `{"status":"ok"}` and is the healthcheck probe.

## Notes

- `server.js` calls `listen(PORT)` without a host, so it binds `::` (IPv4+IPv6) and is
  reachable from the host — no bind-address override is required.
- There are no environment variables or external services, so no secrets are required.
