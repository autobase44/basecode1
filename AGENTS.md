# AGENTS.md

Notes for working in this repository.

## What this repo is

A minimal Node HTTP server (`server.js`, no dependencies, no database, no
environment variables beyond `PORT`) used as a fixture by the Base44 Base Code
end-to-end tests. Its rendered output is asserted by those tests, so treat
`server.js` and the page content as fixed.

## Running it (sandbox / preview)

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- **Do not** run the repo's own `Dockerfile` / `npm start` for development. The
  Dockerfile `COPY`s `server.js` into the image, so any edit would be frozen into
  a stale image. `docker-compose.base44.yml` instead uses a plain `node:22-alpine`
  image with the repo bind-mounted at `/app` and runs `node --watch server.js`,
  so source edits take effect immediately.
- No dependency install step is needed: `package.json` declares no dependencies.
- The container serves on host port 3000 (the preview entry point) and binds
  `::`, so it answers on IPv4 and IPv6.

## Verifying it works

```sh
curl -fsS http://localhost:3000/ | grep 'Base Code E2E'   # page
curl -fsS http://localhost:3000/health                   # {"status":"ok"}
```

A Compose healthcheck polls `GET /health` the same way.
