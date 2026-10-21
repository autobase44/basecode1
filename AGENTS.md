# Notes for working in this repo

## Run in the Base44 sandbox

```bash
docker compose -f docker-compose.base44.yml up -d --build
docker compose -f docker-compose.base44.yml ps
docker compose -f docker-compose.base44.yml logs -f web
```

- The app is served from the cloned source on `node:22-alpine`, with the repo
  bind-mounted at `/app` and started via `node --watch server.js`, so source
  edits reload without an image rebuild.
- The repo's own `Dockerfile` is deliberately **not** used by the Base44
  compose: it `COPY`s the source into the image (a frozen build), which would
  hide any later edit. That file is left untouched because the repo's own e2e
  fixture workflow (`docker build -t base-code-e2e .`) depends on it.
- Host port 3000 is the user-facing entry point (preview).

## Requirements

None. No dependencies (`package.json` has no `dependencies`), no database, no
cache, no external services, and no environment variables. Nothing needs to be
installed before start-up and no secrets are required, so
`/run/base44/app.env` is not wired into the service.

## Verifying it works

- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the page whose heading is `Base Code E2E`
  (`data-testid="e2e-marker"`).

The compose healthcheck asserts both of the above.

## Do not change

The README states this repo is a fixture for Base44 Base Code end-to-end tests
and asks that its content not be changed: the exact page markup, the
`Base Code E2E` heading, `data-testid="e2e-marker"`, and the `/health` JSON
response are asserted by those tests. Keep edits to Base44 setup files
(`docker-compose.base44.yml`, `.base44/`, this file).

## Sandbox configuration

- `BASE44_PREVIEW_MODE` is passed through to the service as a bare pass-through
  entry and is not used by any code in this repo (there is no framework-level
  host/origin gate here). With the flag unset, the app behaves identically.
