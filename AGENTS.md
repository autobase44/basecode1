# Working in this repo

Minimal Node HTTP fixture (no dependencies, no database, no env vars). `server.js`
serves `/` (HTML page) and `/health` (`{"status":"ok"}`).

## Running it in the Base44 sandbox

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

- The service runs `node --watch server.js` from the bind-mounted repo, so source
  edits restart the server automatically — no image rebuild needed.
- `node:20-alpine` is used directly (no image build); `package.json` has no deps,
  so there is nothing to `npm install`.
- Web entry point: host port 3000 → container 3000.

## Verifying

```sh
curl -s http://localhost:3000/health   # {"status":"ok"}
curl -s http://localhost:3000/ | grep 'data-testid="e2e-marker"'
```

## Notes

- The README asks that the app's content stay unchanged: it is a fixture for
  Base44 Base Code E2E tests (`data-testid="e2e-marker"`, exact heading
  "Base Code E2E", `/health` body). Avoid changing page markup or these routes.
- `server.js` deliberately omits a host in `.listen()` so it binds IPv4+IPv6 and a
  `localhost` healthcheck works.
- No external services or credentials are required.
