# Base44 sandbox notes

`base-code-e2e` is a dependency-free Node HTTP fixture (single `server.js`). It is
used by Base44 Base Code E2E tests, so **do not change `server.js`, `package.json`,
`Dockerfile`, or the exact page copy** — the tests depend on the content (heading
`Base Code E2E`, `data-testid="e2e-marker"`, `GET /health` → `{"status":"ok"}`).

## Running here

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- `docker-compose.base44.yml` is the Base44 dev setup: `node:20-alpine` with the
  repo bind-mounted at `/app`, run via `node --watch server.js` (edits to
  `server.js` restart the server automatically), host port `3000:3000`.
- The repo's own `Dockerfile` bakes the source into an image and is production-only;
  it is intentionally not used for the sandbox.
- No dependencies, no database, no environment variables, and no secrets are needed.

## Verify

```sh
curl -sf http://localhost:3000/health           # {"status":"ok"}
curl -sf http://localhost:3000/ | grep 'Base Code E2E'
```
