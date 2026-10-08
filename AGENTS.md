# Agent notes

## Running the app here
- `docker compose -f docker-compose.base44.yml up -d --build`
- The stack is a single `web` service running the checked-out source with
  `node --watch server.js` (bind-mounted at `/app`), so source edits reload
  without a rebuild. There is nothing to install: the app has zero dependencies.
- Public entry point is host port `3000`. The app's own `GET /health` returns
  `{"status":"ok"}` and is used both by the Compose healthcheck and by
  `.base44/environment.json`.

## Things that are not obvious
- `server.js` calls `listen(PORT)` with no host, which binds `::` (dual-stack) —
  that is deliberate so a `localhost`/`127.0.0.1` healthcheck works. Keep it.
- The repository is a fixture for Base44 end-to-end tests; `README.md`,
  `package.json`, `server.js` and `Dockerfile` are intentionally frozen. The
  repo `Dockerfile` bakes the source with `COPY` (a production-style image) and
  is NOT used by `docker-compose.base44.yml`; the compose file runs from source
  so edits stay visible in the preview.

## Verifying it works
- `curl -fsS http://localhost:3000/health` → `{"status":"ok"}`
- `curl -fsS http://localhost:3000/` → HTML containing `data-testid="e2e-marker"`
  and the heading `Base Code E2E`.
