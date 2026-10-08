# Base44 sandbox notes

`base-code-e2e` is a dependency-free single-file Node HTTP server (`server.js`).
The README asks that its content stay exactly as-is — E2E tests depend on the
heading `Base Code E2E` and the `/health` JSON body. Don't change `server.js`,
`package.json`, or the repo `Dockerfile` as part of environment work.

## Running it here

```sh
docker compose -f docker-compose.base44.yml up -d
```

- `docker-compose.base44.yml` runs the app from the cloned source: a plain
  `node:20-alpine` image with the repo bind-mounted at `/app` and
  `node --watch server.js` as the dev command. The repo's own `Dockerfile`
  (which `COPY`s the source into a production image) is deliberately not used,
  because it would freeze the code and hide edits.
- There are no packages to install, no lockfile, no database, and no secrets —
  the app reads no environment variables other than `PORT`.
- `server.js` calls `listen(PORT)` with no host, so it binds IPv4 + IPv6 and
  accepts the preview proxy's external hostname as-is; no host/origin allowlist
  changes were needed.

## Verifying

- `GET /health` → `{"status":"ok"}` (used by the compose healthcheck).
- `GET /` → page containing `data-testid="e2e-marker"` with the text
  `Base Code E2E`.
- Quick check: `curl -s localhost:3000/health && curl -s localhost:3000/ | grep e2e-marker`
- `node --watch` restarts on file changes, so edits to `server.js` appear via
  live reload (no rebuild, no `reload_preview` needed).
