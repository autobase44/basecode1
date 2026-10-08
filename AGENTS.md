# Base44 sandbox notes

This is the `base-code-e2e` fixture: a single dependency-free Node HTTP server (`server.js`).
Do not change its content — the Base Code E2E tests depend on the exact page markup.

## Running it here

- `docker compose -f docker-compose.base44.yml up -d --build`
- Web entry point: host port **3000** (`GET /` serves the page, `GET /health` returns `{"status":"ok"}`).
- The repo's own `Dockerfile` bakes the source via `COPY`, so it is NOT used in the sandbox.
  `docker-compose.base44.yml` runs `node --watch server.js` on a `node:22-alpine` image with the
  repo bind-mounted at `/app`, so edits to `server.js` restart the server automatically.

## Gotchas

- No dependencies, no database, no environment variables, no secrets — nothing to install or migrate.
- `server.js` calls `listen(PORT)` with no host, so it binds all interfaces (IPv4 + IPv6) and works
  behind the preview proxy without extra host configuration.
- Live reload uses Node's built-in `--watch`; if a change ever doesn't appear, run `reload_preview`.

## Verifying

- `curl -fsS http://localhost:3000/health` → `{"status":"ok"}`; `curl -s http://localhost:3000/` →
  page containing `data-testid="e2e-marker"` and the heading "Base Code E2E".
