# Notes for agents working in this repo

## What this is

A minimal Node HTTP server (`server.js`, no dependencies) used as a fixture by
Base44 Base Code end-to-end tests. **Its content is load-bearing — the tests
depend on the exact heading and routes. Do not change `server.js`, `package.json`
or the `Dockerfile` unless the task is explicitly about them.**

## Running it in the Base44 sandbox

`docker-compose.base44.yml` is the runbook; the repo's own `Dockerfile` builds a
production image (`COPY`-baked source) and is NOT used for the preview.

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- The service runs `node --watch server.js` from the bind-mounted checkout, so
  edits to `server.js` reload in place. No separate restart needed.
- Node's `--watch` polls the filesystem; it works over the bind mount here.
- No dependencies, no database, no migrations, no env vars or secrets are
  required to boot. `PORT` is set to `3000` in compose.

## Verifying it works

```sh
curl -fsS http://localhost:3000/health   # {"status":"ok"}
curl -fsS http://localhost:3000/ | grep -o 'data-testid="e2e-marker"'
```

Both must pass; a bare HTTP 200 on `/` is not enough — the page must contain the
`e2e-marker` heading.

## Gotchas

- `server.js` intentionally calls `listen(PORT)` with no host argument, so it
  binds both IPv4 and IPv6 — required for a `localhost` healthcheck to work.
- There is no test suite in the repo; the E2E tests live in the Base44 test
  harness, not here.
