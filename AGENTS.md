# Agent notes — base-code-e2e

## Run it here

```bash
docker compose -f docker-compose.base44.yml up -d --build
curl -s http://localhost:3000/health   # {"status":"ok"}
```

Host port 3000 is the public preview entry point.

## Non-obvious things

- **Do not change `server.js`.** This repo is a fixture for the Base44 Base Code
  E2E tests; the README asks that its content stay exactly as it is. The
  `data-testid="e2e-marker"` heading and the exact `{"status":"ok"}` response are
  what the tests assert.
- **The repo's `Dockerfile` is not used by the sandbox compose.** It does
  `COPY package.json server.js ./`, i.e. it bakes the source into an image, so
  edits would not show in the preview. `docker-compose.base44.yml` instead runs
  `node:20` with the repo bind-mounted at `/app`.
- **No dependencies, no database, no environment variables.** `package.json`
  declares no dependencies, so there is no install step in the compose startup
  flow, and nothing needs `/run/base44/app.env`.
- **Live reload** comes from `node --watch server.js` (Node's built-in watcher,
  available in Node 20) — editing `server.js` restarts the server in place.
- The server listens without an explicit host, which binds `::` for both IPv4
  and IPv6, so a `localhost` healthcheck works. Keep it that way.
- The healthcheck in compose calls the app's *existing* `/health` route using
  `node -e` (no curl/wget needed in the image). Do not add endpoints for it.

## Verify

- `GET /` → page with the heading `Base Code E2E`.
- `GET /health` → `{"status":"ok"}`.
