# base-code-e2e — Base44 sandbox notes

Minimal Node HTTP app (no dependencies, no database, no environment variables).
The repo README asks that the app's exact content stay unchanged — the E2E tests
depend on it. Keep setup changes to sandbox tooling only.

## Running it here

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- Web entry point: host port **3000** → container 3000.
- The service uses a plain `node:20-alpine` image with the repo bind-mounted at
  `/app`, running `node --watch server.js`, so source edits apply without a
  rebuild. The repo's own `Dockerfile` bakes the source via `COPY` and is
  deliberately not used.
- No `npm install` step: `package.json` declares no dependencies.

## Verifying it works

```sh
curl -s localhost:3000/health   # {"status":"ok"}
curl -s localhost:3000/         # HTML page with heading "Base Code E2E"
```

The compose healthcheck probes the existing `/health` route, so
`docker compose -f docker-compose.base44.yml ps` shows `healthy` once the server
is accepting requests.

To confirm the container is really serving the repo source (not a baked copy):
`diff <(docker compose -f docker-compose.base44.yml exec -T web cat /app/server.js) server.js`.

## Quirks

- `PORT` defaults to 3000 in `server.js`; the compose file sets it explicitly.
- `server.js` listens without a host argument, so it binds IPv4+IPv6 and a
  `localhost` healthcheck works.
