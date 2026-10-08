# Base44 dev environment

## Run it

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

Web entry point: <http://localhost:3000> (`GET /` = the page, `GET /health` = `{"status":"ok"}`).

## Notes

- Dependency-free Node http server (`server.js`); no database, no environment variables, no
  external services or credentials.
- The compose service uses the plain `node:20-alpine` image with the repo bind-mounted at
  `/app` and runs `node --watch server.js`, so source edits reload without a rebuild. The
  repo's own `Dockerfile` is a production image (`COPY`) and is NOT used by the dev compose.
- `server.js` listens without a host argument, so it binds `::` (IPv4 + IPv6) — keep it that
  way, or a `localhost` healthcheck resolving to `::1` will fail.
- Verify the app: `curl -s localhost:3000/health` and check the page at `/` shows the
  heading "Base Code E2E".

## Tests

No test suite in the repo.
