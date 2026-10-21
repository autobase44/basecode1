# Base44 sandbox setup

This repo is an intentionally minimal fixture app (see README.md — its content is
relied on by end-to-end tests, so don't change the page markup or the endpoints).

## Running it here

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- Single service `web`: `node:20-alpine` with the repo bind-mounted at `/app`,
  started as `node --watch server.js` on host port **3000**.
- The repo's own `Dockerfile` is **not** used for the sandbox: it `COPY`s the
  source into a production image, which would freeze the code and hide edits.
- No dependencies to install, no database, no migrations, no environment
  variables and no external credentials.
- `BASE44_PREVIEW_MODE` is passed through as a bare Compose `environment:` entry.
  The app itself does not read it; nothing is gated on it. With the variable
  unset, behaviour is identical to any normal local run.

## Verifying

```bash
curl -s localhost:3000/health   # {"status":"ok"}
curl -s localhost:3000/ | grep e2e-marker
```

The container healthcheck probes the same `/health` endpoint with `node`'s global
`fetch` (`curl` is not present in the alpine image).

## Editing loop

`node --watch` restarts the server on file changes, so backend edits apply
without a rebuild; the preview iframe needs `reload_preview` only when the HTTP
listener itself is replaced.
